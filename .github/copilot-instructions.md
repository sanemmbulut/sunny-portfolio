# Copilot instructions for this repository

This file is a short, actionable guide to help an AI coding agent be immediately productive editing and building this project.

Key points (read before editing):

- Project type: static site template (Bootstrap + Sass) with Handlebars-like layouts powered by Panini and a Gulp build pipeline.
- Source of truth: `src/` — always change files under `src/`. `dist/` and `assets/` are generated output and can be overwritten by builds.

Useful entry points and examples

- Build & dev
  - Dev (watch + BrowserSync): `gulp dev` (runs the `dev` task in `gulpfile.js`). This watches `src/` and serves `dist/`.
  - Production build: `gulp prod` (minifies CSS/JS/images and writes optimized output to `dist/`).
  - Note: `package.json` has no npm scripts; prefer `npx gulp dev` to avoid requiring a global gulp install.

- Templates & content
  - Panini layouts are under `src/layouts/` (e.g. `src/layouts/default.html`). Templates use Panini/Handlebars-style tokens (e.g. `{{title}}`, `{{> navigation}}`).
  - Pages: `src/pages/` — these are compiled into `dist/` by Panini.
  - Partials: `src/partials/` (navigation, footer, etc.).
  - Data: `src/data/data.json` provides JSON data to templates.

- Styles & scripts
  - SCSS entry points: `src/assets/scss/main.scss` and `src/assets/scss/rtl.scss`. The gulp task `compileSCSS` compiles these into `dist/assets/css`.
  - Custom JS: `src/assets/js/custom.js` compiled by `compileJS` into `dist/assets/js/`.
  - Vendor files: `src/assets/vendor/js/` and `src/assets/vendor/css/` — `concatScripts` determines the concat order (jquery, popper, bootstrap, etc.).

- Linting & checks
  - SCSS lint: `gulp scssLint` (configured via `.scss-lint.yml`).
  - HTML lint: `gulp htmlLint` (uses `gulp-htmllint`).
  - JS lint: `gulp jsLint` (uses JSHint on `src/assets/js/*.js`).

Project conventions and gotchas (do not assume defaults)

- Do not edit `dist/` directly — changes must be made in `src/` and then built.
- `package.json` contains devDependencies only; there are no npm scripts. Use `npm install` then `npx gulp dev` (or `gulp dev` if the user has gulp CLI installed globally).
- Templates use Panini (flat-file generator), not a server-side framework. When editing templates, remember to update partials or data files used by many pages.
- The HTML layout uses `{{root}}` and `{{> partial}}` patterns; changes to `src/layouts/default.html` affect all pages.

Where to look for examples in this repo

- `src/layouts/default.html` — base layout and token examples.
- `src/pages/*.html` — page-level usage of layouts and page content.
- `src/partials/` — navigation, footer, and other reusable fragments.
- `gulpfile.js` — canonical source for build tasks and pipeline order (compileSCSS, compileHTML, compileJS, concatScripts, minifyCss, etc.).

How to make safe edits (minimal checklist)

1. Modify code under `src/` (templates, scss, js, data).
2. Run `npm install` once if dependencies missing.
3. Build and test locally with `npx gulp dev` and check BrowserSync at localhost:3000.
4. For production verification run `npx gulp prod` and inspect `dist/`.

If anything is missing or unclear here, ask for the file or behavior to inspect and I will update these instructions.

---
Files referenced above: `package.json`, `gulpfile.js`, `src/layouts/default.html`, `src/pages/`, `src/partials/`, `src/assets/scss/main.scss`, `src/assets/js/custom.js`, `src/data/data.json`.
