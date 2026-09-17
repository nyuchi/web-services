# Nyuchi Web Services

> The static showcase site at services.nyuchi.com — a single page listing
> Nyuchi's projects and tools.

[![Lint](https://github.com/nyuchi/web-services/actions/workflows/lint.yml/badge.svg)](https://github.com/nyuchi/web-services/actions/workflows/lint.yml)
![GitHub Pages](https://img.shields.io/badge/GitHub_Pages-deployed-222222?style=flat-square&logo=githubpages&logoColor=white)
![Static](https://img.shields.io/badge/Stack-HTML_+_CSS-E34F26?style=flat-square&logo=html5&logoColor=white)

**Live:** [services.nyuchi.com](https://services.nyuchi.com) | **Deploy:** GitHub Pages on push to `main` | **Status:** unchanged since December 2025

---

## What it is

Two files and a CNAME: `index.html` (360 lines) and `styles.css` (817 lines).
There is no build step, no framework and no JavaScript bundle. GitHub Pages
serves it at [services.nyuchi.com](https://services.nyuchi.com) whenever `main`
changes.

The page introduces [Nyuchi](https://www.nyuchi.com) — a Pan-African technology
company based in Harare, Zimbabwe — and lists its projects as cards linking to
their GitHub repositories.

Nothing substantive has changed here since 16 December 2025.

## Local development

Open `index.html` in a browser. That is the whole workflow.

## Maintenance notes

The page and this README have both drifted from what is true elsewhere in the
estate. Three things to know before editing:

### The project links point at a GitHub org that no longer exists

Every project card in `index.html` links to `github.com/nyuchitech/<repo>`. The
`nyuchitech` organisation was renamed to `nyuchi`, so the organisation URL
itself is now a 404. Individual repository URLs still work because GitHub
redirects renamed owners, but they should be rewritten to `github.com/nyuchi/`.
Two of them do not redirect anywhere, because the repositories no longer exist
under those names: `nyuchitech/nyuchi-main` and `nyuchitech/mukoko-docs`.

### The palette is 21 colour families, and all seven minerals are here

The shared palette has **21 colour families** in three groups of seven:

| Group        | Count | Families                                                         |
| ------------ | ----: | ---------------------------------------------------------------- |
| Minerals     |     7 | cobalt, tanzanite, malachite, gold, terracotta, sodalite, copper |
| Heritage     |     7 | indigo, savanna, baobab, sunset, river, hematite, kalahari       |
| Experimental |     7 | ember, acacia, fern, lagoon, storm, dusk, protea                 |

`styles.css` used to define five minerals and label them "Five African
Minerals" — a known bug that propagated through several repositories. It now
carries all seven; sodalite and copper take their values from the Mzizi design
system.

The site ships **dark mode only**: `--gold`, `--malachite` and the rest alias
the `-dark` tokens unconditionally, and `body` uses `--bg-dark`. The `-light`
tokens are defined for reference but never render, so only the dark column
describes what a visitor actually sees.

Contrast is measured against those grounds rather than asserted. AAA is 7:1;
AA normal text is 4.5:1.

| Mineral    | Dark token | On charcoal |          | Light token | On cream |            |
| ---------- | ---------- | ----------: | -------- | ----------- | -------: | ---------- |
| gold       | `#FFD740`  |     14.19:1 | AAA      | `#5D4037`   |   8.84:1 | AAA        |
| malachite  | `#64FFDA`  |     15.89:1 | AAA      | `#004D40`   |   9.33:1 | AAA        |
| cobalt     | `#00B0FF`  |      8.16:1 | AAA      | `#0047AB`   |   8.01:1 | AAA        |
| tanzanite  | `#B388FF`  |      7.43:1 | AAA      | `#4B0082`   |  12.29:1 | AAA        |
| terracotta | `#D4A574`  |      8.89:1 | AAA      | `#8B4513`   |   6.74:1 | AA only    |
| sodalite   | `#3D5AFE`  |      3.86:1 | not text | `#283593`   |   9.86:1 | AAA        |
| copper     | `#FF8A65`  |      8.56:1 | AAA      | `#BF5A36`   |   4.21:1 | large only |

Two entries are worth stating plainly rather than burying:

- **`--sodalite-dark` is not safe for text.** At 3.86:1 it fails AA for normal
  text, let alone AAA. Use it for borders, fills and large shapes on AI and
  Shamwari surfaces. The comment beside the token says so.
- **`--terracotta-light` was documented as 7.2:1 and measures 6.74:1.** It has
  never met the AAA claim the file made for it. Light mode does not render, so
  nothing is broken today, but the number was wrong and is now correct.

### Terracotta has drifted from the design system

The Mzizi design system gives terracotta as `#A0522D` light / `#E1B07E` dark;
this site carries `#8B4513` / `#D4A574`. The site's values are left in place
because Mzizi's light value measures 5.33:1 on cream — worse than the one here.
Aligning them is a design-system decision, not a site fix, and is deliberately
left open.

### The npm packages listed here were wrong

The previous version of this README told readers to run
`npm install @nyuchi/theme @nyuchi/ui @nyuchi/ubuntu` and gave version numbers
for all three. Checked against the registry:

| Package          | Registry state           | Previously claimed |
| ---------------- | ------------------------ | ------------------ |
| `@nyuchi/theme`  | **Does not exist** (404) | v2.0.0             |
| `@nyuchi/ui`     | Published, latest 0.1.2  | v1.0.0             |
| `@nyuchi/ubuntu` | Published, latest 1.0.0  | v1.0.0             |

The install line has been removed rather than corrected, because a third of it
cannot be installed.

### Dead links removed from this README

`brand.nyuchi.com` does not resolve and `assets.nyuchi.com` returns 404. Both
were listed under "Resources" and have been removed.

## Licence

The repository ships **no LICENSE file** and GitHub reports no licence for it.
Treat the content as all rights reserved until one is added.

© Nyuchi Africa (PVT) Ltd, Harare, Zimbabwe.
