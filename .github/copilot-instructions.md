<!-- GitHub Copilot / AI Agent instructions for this repository -->
# Repository-specific AI agent instructions

Purpose
- This is a small, static single-page website. The goal of this document is to give an AI coding agent the exact, actionable context it needs to be productive editing or extending the site.

Big picture
- A single HTML entry point: `index.html` — presents the UI and loads Bootstrap from CDNs.
- Custom styling lives in `index.css` (root). Note: `index.html` currently links to `styles.css` — keep this mismatch in mind when editing; either update the HTML link or the filename to keep them consistent.
- No build system, no package.json, no backend services. Changes can be verified by opening `index.html` in a browser or serving the folder with a simple HTTP server.

Key files to inspect
- `index.html` — main page, includes Bootstrap via CDN and inline script tags for Bootstrap/Popper.
- `index.css` — custom styles (responsive nav, toggling, colors, typography).

Developer workflows (discoverable)
- Quick local preview: open `index.html` directly in a browser, or from project root run:
  ```powershell
  python -m http.server 8000; Start-Process http://localhost:8000
  ```
  (PowerShell example — the first command starts the server; the second opens the browser.)
- There is no build step or automated tests found in the repo. Treat edits as immediately deployable assets.

Conventions & useful patterns (from the codebase)
- Styling: keep all custom rules in `index.css`. Example: responsive navigation uses `.menu-toggle` to toggle `.nav-links.active`.
- UI framework: Bootstrap 5 is used from CDN in `index.html` — use its utility classes for layout and spacing rather than adding redundant CSS when possible.
- Resource links: external dependencies are CDN links in `index.html` (Bootstrap CSS/JS and Popper). Do not change CDN integrity attributes unless updating to a newer, intentional version.
- Filenames: prefer conservative changes — if you rename `index.css` to `styles.css` (or vice-versa), update the HTML link and search for references before committing.

Examples of common tasks
- Add a new header section:
  - Edit `index.html` to add semantic markup (e.g., `<header>`, `<section>`).
  - Add styles to `index.css`. Keep selectors minimal and prefer BEM-like or semantic class names.
- Fix the style-link mismatch:
  - Option A: update the `<link rel="stylesheet" href="styles.css">` in `index.html` to `href="index.css"`.
  - Option B: rename `index.css` to `styles.css` and update any references.

Integration points and constraints
- No server-side integrations discovered. All dynamic behavior is client-side (Bootstrap JS).
- Keep CDN usage stable — changing to a local copy is acceptable but note larger repo changes are required.

Editing guidelines for AI agents
- Make minimal, focused changes per PR: one logical concern per commit.
- Preserve existing class names and Bootstrap usage unless refactoring deliberately; explain broad refactors in the PR description.
- When adding CSS, prefer adding small, scoped rules to `index.css` rather than large global overrides.
- Before renaming files, check `index.html` and any other files for references to avoid broken links.

If unsure
- Ask for a short confirmation before large refactors (renaming files, replacing Bootstrap, or introducing a build tool).

Where to start
- Inspect `index.html` and `index.css` first. The most common changes involve layout, nav behavior, and content text.

Next steps / Feedback
- If any sections here are unclear or you want more detail about a particular workflow (e.g., how to run a live-reload server, or preferred commit message format), tell me and I will expand this file.
