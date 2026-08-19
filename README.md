# Citizen Help Hub – Pune

Static HTML/CSS website with citizen information for Pune: About, Tourism, Hospitals, Police, Government Schemes, and Emergency.

There is **no JavaScript framework, no build step, and no backend**. Pages are plain HTML. Open `index.html` in a real browser (Chrome, Safari, Firefox). Cursor’s in-editor HTML preview does **not** follow links between pages.

## Project structure

```
index.html                 # Home — only HTML file at the project root
css/
  style.css                # Shared: reset, header, nav, footer, buttons
  home.css                 # Home page only
  about-pune.css           # About Pune page only
  tourism.css              # Tourism page only
images/                    # Photos used by Tourism cards (and later pages)
pages/
  about-pune.html          # Ready
  tourism.html             # Ready
  hospitals.html           # Placeholder
  police.html              # Placeholder
  government-schemes.html  # Placeholder
  emergency.html           # Placeholder
```

**Do not put inner pages next to `index.html`.** Home stays at the root. Every other page lives in `pages/`.

## Path rules (must follow)

These relative paths are required. Wrong paths break navigation and CSS.

### From `index.html` (root)

| Asset / page | Path |
| --- | --- |
| Shared CSS | `css/style.css` |
| Home CSS | `css/home.css` |
| Inner page | `pages/tourism.html`, `pages/about-pune.html`, … |

### From any file in `pages/`

| Asset / page | Path |
| --- | --- |
| Shared CSS | `../css/style.css` |
| Page CSS | `../css/about-pune.css` or `../css/tourism.css` |
| Images | `../images/filename.jpg` |
| Home | `../index.html` |
| Another inner page | `tourism.html` (same folder, no `pages/` prefix) |

Example nav on an inner page:

```html
<a href="../index.html">Home</a>
<a href="about-pune.html">About Pune</a>
<a href="tourism.html">Tourism</a>
```

Example nav on Home:

```html
<a href="index.html">Home</a>
<a href="pages/about-pune.html">About Pune</a>
<a href="pages/tourism.html">Tourism</a>
```

## CSS rules

- **No CSS inside HTML `<style>` tags.** Use files in `css/`.
- **`css/style.css` is shared.** Header, navigation, footer, `.btn`, and `.coming-soon` belong here so every page looks the same.
- **Page-specific layout goes in its own file** (`home.css`, `about-pune.css`, `tourism.css`). Do not dump page-only card/section styles into `style.css`.
- Link CSS in `<head>`:

```html
<link rel="stylesheet" href="../css/style.css">
<link rel="stylesheet" href="../css/tourism.css">
```

- Keep the existing visual language: blue/teal header (`#1e3a8a`, `#087f8f`), navy nav/footer (`#172554`), gold hover (`#ffd166`), light page background (`#f4f7fb`).
- Mark the current page in the nav with `class="active"`.

## HTML / naming rules

- Filenames: **lowercase kebab-case** (`about-pune.html`, `government-schemes.html`). Do not use `About.html` or `Tourism.html`.
- Every page uses the same header text: **Citizen Help Hub – Pune**.
- Every page uses the same nav items, in this order: Home, About Pune, Tourism, Hospitals, Police, Government Schemes, Emergency.
- If you add or rename a page, **update the nav on every HTML file** (root + all of `pages/`). Also add a card on `index.html`.
- Placeholder pages use the shared `.coming-soon` block until real content exists.
- Keep content suitable for a student/civic info site: clear English, maps links may open in a new tab (`target="_blank"` + `rel="noopener"`).

## Adding a new page

1. Create `pages/new-page.html` (copy header/nav/footer from an existing page).
2. Use `../css/style.css`. Add `css/new-page.css` only if that page needs unique layout.
3. Add the nav link on **all** pages (see path rules above).
4. Add a home card in `index.html` pointing to `pages/new-page.html`.
5. Put images in `images/` and reference them as `../images/...` from the new page.

Do not create a second copy of a page at the project root.

## Images

- Store files in `images/`.
- Tourism currently expects files such as `shaniwar-wada.jpg`, `aga-khan-palace.jpg`, `lal-mahal.jpg`. Missing files show as broken images until they are added.
- Prefer descriptive kebab-case names. Always set `alt` text.

## How to preview

Open **`index.html` in a real browser**, then use the nav. Do not rely on Cursor/VS Code HTML preview for clicking between pages.

Optional local server from the project root:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Page status

| Page | Status |
| --- | --- |
| Home (`index.html`) | Done |
| About Pune | Done |
| Tourism | Done (add photos in `images/`) |
| Hospitals | Placeholder |
| Police | Placeholder |
| Government Schemes | Placeholder |
| Emergency | Placeholder |

## What not to do

- Do not flatten `pages/` back to the root.
- Do not use Windows paths (`D:\...`) or Android `content://` URIs in `href`.
- Do not inline large CSS in HTML.
- Do not change shared header/nav styling on only one page; change `css/style.css` instead.
- Do not add a JS framework unless the user asks.
