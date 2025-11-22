<!-- .github/copilot-instructions.md: Guidance for AI coding agents working on this repo -->
# Copilot instructions — git-test

Purpose: make an AI coding agent immediately productive in this tiny static-site repo.

- **Big picture**: This repository is a simple static HTML site (no build system). Primary pages are `index.html`, `peanutbutter.html`, and `recipe.html`. There is an `assets/` convention used by `peanutbutter.html` for images/audio. JavaScript is inline and minimal (theme toggle + small event handlers).

- **Key files**:
  - `index.html` — landing page placeholder.
  - `peanutbutter.html` — the most complete page; shows styling patterns, responsive grid, theme toggle (uses `data-theme` on `html` and `localStorage`), and accessible controls (`aria-*`).
  - `recipe.html` — simple content page with lists and steps.
  - `README.md` — very small; no CI/build instructions present.

- **Patterns & conventions to follow**:
  - Small, self-contained pages: prefer minimal, in-file CSS/JS unless asked to refactor into modules.
  - Theme handling: the UI uses `document.documentElement.setAttribute('data-theme', ...)` and stores the value under `localStorage['theme']`. If modifying theme behavior, update both `peanutbutter.html` script and any other pages that should share the convention.
  - Assets: place images/audio under `assets/` and reference them with relative paths (examples in `peanutbutter.html`). Do not add proprietary/copyrighted media without explicit user instruction.
  - Accessibility: existing pages use `aria-label`, `aria-pressed`, and semantic headings. Preserve or enhance these when editing.

- **Local dev / testing workflows**:
  - There is no build/test toolchain. To serve locally for browser testing run (PowerShell):

    ```powershell
    python -m http.server 8000
    # then open http://localhost:8000/index.html
    ```

  - Alternatively, use VS Code Live Server if available.

- **Common edits & examples**:
  - Add a new HTML page `foo.html`: create the file, copy the structure from `peanutbutter.html` (head styles + container), and link it from `index.html` with a relative anchor:

    ```html
    <!-- add to index.html navigation area -->
    <a href="foo.html">Foo</a>
    ```

  - Update theme behavior example (read/write key): `localStorage.setItem('theme', next)` and `localStorage.getItem('theme')`.

- **What not to assume**:
  - There is no package.json, no npm/yarn, no test runner, and no server-side code. Do not introduce a build system unless the user requests it.
  - No CI configuration present; do not add CI changes without the user's approval.

- **PR and commit guidance for agents**:
  - Keep changes small and focused (one page or one refactor per PR).
  - When adding JS or assets, include a brief note in the PR describing why and how to test locally (e.g., port used by `python -m http.server`).

If anything in these instructions is unclear or you want additional patterns (e.g., extract CSS into a shared file, or add a basic dev server), tell me which direction to take and I'll update this document.
