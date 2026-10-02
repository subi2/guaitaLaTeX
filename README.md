# guaitaLaTeX

**Editor i visor de LaTeX en un sol fitxer HTML**, de la suite [Guaita Apps](https://github.com/subi2/guaitaApps).
Escriu LaTeX, mira'n el resultat al moment i gestiona la bibliografia sense instal·lar res. Tot s'executa al navegador, fora de línia.

`v1.1` · [AGPL-3.0-only](#llicència) · JavaScript pur, sense CDN · [English below](#english)

---

## Característiques

- **Editor amb ressaltat de sintaxi**, números de línia, pestanyes i cerca/reemplaça amb expressions regulars.
- **Vista prèvia en directe** amb [KaTeX](https://katex.org): seccions, llistes, taules, flotants, equacions numerades, teoremes, macros, colors, cites i bibliografia.
- **Edició assistida de LaTeX**
  - Autocompletat d'ordres, entorns, claus de cita, etiquetes i paquets (`Ctrl`+`Espai` el força).
  - Fragments amb camps navegables amb `Tab`.
  - Autotancament de `{ ( [ $` i dels entorns; `Intro` dins d'una llista continua amb `\item`.
  - Ressaltat de claus i de parelles `\begin`/`\end`.
  - Vista prèvia flotant de la fórmula sota el cursor.
  - Operacions de línia, transformacions (majúscules, escapament, cometes, accents), alineació de columnes `&` i envoltar en un entorn.
  - Vés a la definició (`F12`) i reanomena etiqueta o clau a tot el document.
- **Biblioteca bibliogràfica**: importa `.bib`, `.ris` i CSL-JSON; formulari per tipus, detecció de duplicats, comprovació de cites i exportació a `.bib`, HTML o text.
- **GitHub**: obre fitxers d'un repositori i desa'ls amb commit, amb detecció de conflictes per `sha`.
- **Enllaç amb [guaitaCorpus](https://github.com/subi2/guaitaApps)**: cita entrades de Corpus i obre-les de tornada (protocol `postMessage`, versió 1).
- **Temes**: interfície fosca (Caixetí), clara o segons el sistema, amb paper de la vista prèvia fosc o clar de manera independent. Els colors explícits del document s'adapten al paper.
- **Català i anglès** a la mateixa interfície (Visualitza → Idioma / Language).
- **Exporta** a `.tex`, pàgina HTML autònoma (amb MathML), text pla i PDF (impressió del navegador).

## Inici ràpid

1. Descarrega `guaitaLaTeX_v1.1.html` i obre'l amb Chrome, Edge, Firefox o Safari. No cal servidor ni instal·lació.
2. La primera vegada es carrega un document de demostració i una biblioteca amb tres entrades.
3. Tot és accessible des dels menús; les dreceres són opcionals. Al Mac, `Ctrl` equival a `⌘` i `Alt` a `⌥`.

Per obrir l'ajuda HTML des de **Ajuda → Manual d'ús (HTML)**, deixa aquests fitxers a la mateixa carpeta que l'aplicació:

| Fitxer | Contingut |
|---|---|
| `guaitaLaTeX_v1.1.html` | L'aplicació |
| `HLP guaitaLaTeX-ajuda.html` | Manual d'ús en català |
| `HLP guaitaLaTeX-en-ajuda.html` | User guide in English |
| `guaitaCorpus.html` | (opcional) per a l'enllaç amb Corpus |

**Ajuda → Ajuda ràpida** funciona sempre, encara que els manuals no hi siguin.

## Dreceres principals

| Drecera | Acció |
|---|---|
| `Ctrl`+`S` / `Ctrl`+`O` | Desa / obre |
| `Alt`+`N` / `Alt`+`W` | Nova pestanya / tanca la pestanya |
| `Ctrl`+`Alt`+`S` | Desa a GitHub |
| `Ctrl`+`F` / `Ctrl`+`H` / `Ctrl`+`G` | Cerca / reemplaça / vés a la línia |
| `Ctrl`+`/` | Comenta o descomenta |
| `Ctrl`+`Espai` | Autocompleta |
| `F12` | Vés a la definició (etiqueta o cita) |
| `Alt`+`↑` / `Alt`+`↓` | Mou la línia |
| `Ctrl`+`Maj`+`K` / `Ctrl`+`J` / `Ctrl`+`Maj`+`D` | Suprimeix / uneix / duplica la línia |
| `Ctrl`+`Intro` | Renderitza ara |

La llista completa és a **Ajuda → Dreceres de teclat**.

## Límits

guaitaLaTeX **no és un motor TeX complet**: és una aproximació pensada per revisar contingut, fórmules i referències.

- Entorns com `tikzpicture` es mostren com a codi.
- Les imatges externes (`\includegraphics`) es mostren com a marcador, perquè l'app és autònoma.
- `\input` i `\include` no es poden carregar.
- La paginació no és la de LaTeX, i els paquets que no coneix s'avisen al panell d'errors.

Per al document final, compila amb LaTeX.

## Privadesa i seguretat

- **Tot és local**: el document, la biblioteca i les preferències es queden al navegador. No hi ha servidor, analítica ni recursos externs.
- Una **política de seguretat de contingut (CSP)** només permet executar els scripts de l'app (verificats per hash) i limita la xarxa a `api.github.com`.
- El text d'un document no pot executar codi: els enllaços es limiten a `http`, `https` i `mailto`, i els colors i mides es validen.
- **Token de GitHub**: usa un token *fine-grained* amb permís `Contents: Read and write` només sobre el teu repositori. Per defecte viu a la sessió del navegador; si marques «Recorda», es desa sense xifrar: no ho facis en un ordinador compartit.
- L'enllaç amb Corpus valida l'URL i l'origen dels missatges. Es rebutgen fitxers de més de 25 MB.
- Les dades es guarden amb `localStorage`: esborrar les dades del lloc les elimina. Exporta la biblioteca a `.bib` de tant en tant.

## Navegadors

Qualsevol navegador modern. Desar directament sobre el fitxer original requereix l'API File System Access (Chrome, Edge); a Firefox i Safari l'app descarrega el fitxer.

## Llicència

© 2026 Jordi Subirós. Programari lliure sota la **GNU Affero General Public License v3.0 només** (`AGPL-3.0-only`). El fitxer HTML és, alhora, el codi font de l'aplicació (excepte KaTeX, que hi va minificat). Si l'executes com a servei accessible per xarxa, l'AGPL t'obliga a oferir el codi font als usuaris. Consulta el fitxer `LICENSE` del repositori.

Components de tercers incrustats (els textos complets són a **Ajuda → Llicència i avisos**):

- [KaTeX](https://katex.org) — llicència MIT, © 2013–2020 Khan Academy i col·laboradors.
- [IBM Plex](https://github.com/IBM/plex) — SIL Open Font License 1.1, © 2019 IBM Corp.

> Guaita Apps es distribueix «tal com és», sense cap garantia. Les eines estan pensades desde la recerca i com a suport tècnic i educatiu; la verificació dels resultats i la responsabilitat derivada del seu ús recauen únicament sobre l'usuari final.

SBS BIM Consulting 2026

---

## English

**guaitaLaTeX** is a **single-file LaTeX editor and viewer** from the [Guaita Apps](https://github.com/subi2/guaitaApps) suite. Write LaTeX, see the result instantly and manage your bibliography without installing anything. Everything runs in your browser, offline.

### Features

- Syntax-highlighted editor with line numbers, tabs and regex find/replace.
- Live preview with [KaTeX](https://katex.org): sections, lists, tables, floats, numbered equations, theorems, macros, colours, citations and bibliography.
- Assisted editing: autocomplete for commands, environments, citation keys, labels and packages; snippets with `Tab` stops; auto-closing of `{ ( [ $` and environments; matching brace and `\begin`/`\end` highlighting; floating formula preview; line operations and text transforms; `&` column alignment; go to definition (`F12`); rename label or key.
- Bibliographic library: import `.bib`, `.ris` and CSL-JSON; per-type form, duplicate detection, citation check, export to `.bib`, HTML or text.
- GitHub: open and commit files from a repository, with conflict detection by `sha`.
- Link with guaitaCorpus (`postMessage` protocol, version 1).
- Dark (Caixetí), light or system theme, with independent dark or light preview paper; explicit document colours adapt to the paper.
- Catalan and English in the same interface (View → Idioma / Language).
- Export to `.tex`, standalone HTML (with MathML), plain text and PDF (browser print).

### Quick start

1. Download `guaitaLaTeX_v1.1.html` and open it in Chrome, Edge, Firefox or Safari. No server or installation needed.
2. Keep `HLP guaitaLaTeX-ajuda.html` and `HLP guaitaLaTeX-en-ajuda.html` in the same folder to open the HTML guides from **Help → User guide (HTML)**. **Help → Quick help** always works.
3. Everything is reachable from the menus; shortcuts are optional. On a Mac, `Ctrl` means `⌘` and `Alt` means `⌥`.

### Limits

This is **not a full TeX engine**. `tikzpicture` and similar environments are shown as code, external images as placeholders, and `\input`/`\include` cannot be loaded. Pagination differs from LaTeX. Compile with LaTeX for the final document.

### Privacy and security

Everything stays in your browser: no server, analytics or external resources. A content security policy allows only the app's own scripts (verified by hash) and restricts the network to `api.github.com`. Use a fine-grained GitHub token with `Contents: Read and write` on a single repository; by default it lives only in the browser session.

### Licence

© 2026 Jordi Subirós. Free software under the **GNU Affero General Public License v3.0 only** (`AGPL-3.0-only`). The HTML file is also the application's source code (except KaTeX, which is minified). See the `LICENSE` file. Bundled third-party components: KaTeX (MIT) and IBM Plex (SIL OFL 1.1); full texts under **Help → Licence and notices**.

> Guaita Apps is distributed “as is”, without any warranty. The tools are conceived from research and as technical and educational support; verification of the results and any responsibility arising from their use rest solely with the end user. *(English translation of the Catalan notice above.)*
