# obgs-hs.github.io

Official documentation portal for the [OBGS](https://github.com/obgs-hs) (**O**pen **B**oard **G**ame **S**heets) ecosystem.

Hosted live at **[https://obgs-hs.github.io/](https://obgs-hs.github.io/)**.

---

## Structure

The portal compiles and aggregates Haddock documentation across the OBGS suite into a single unified website:

| Package | Status | Documentation Path | Source Repository |
| --- | --- | --- | --- |
| **`obgs-type-level`** | Released (`v0.1.0.0`) | [`/type-level/`](https://obgs-hs.github.io/type-level/) | [`obgs-hs/type-level`](https://github.com/obgs-hs/type-level) |
| **`obgs-data`** | Upcoming | `/data/` | *(in development)* |
| **`obgs-control`** | Upcoming | `/control/` | *(in development)* |
| **`obgs-form`** | Upcoming | `/form/` | *(in development)* |

---

## How It Works

This repository is lightweight: it contains the portal landing page (`index.html`), branding assets (`assets/`), and a GitHub Actions workflow (`.github/workflows/deploy.yml`).

When the workflow runs:
1. It checks out the published component packages (currently `obgs-hs/type-level`).
2. Generates hyperlinked Haddock documentation using GHC 9.14.1 and Cabal 3.16.
3. Assembles the landing page and package documentations into `public/`.
4. Deploys the static site directly to GitHub Pages via native artifacts (no extra git commits).

---

## GitHub Pages Configuration

To activate the portal after creating the `obgs-hs/obgs-hs.github.io` repository on GitHub:

1. Navigate to **Settings** &rarr; **Pages**.
2. Under **Build and deployment** &rarr; **Source**, select **`GitHub Actions`**.
3. Push to `main` (or click **Actions** &rarr; **Deploy Documentation Portal** &rarr; **Run workflow**).

---

## Adding New Packages

When a new package (e.g. `obgs-hs/data`) is given its own repository:
1. Add its checkout step in [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml).
2. Add its `cabal haddock` and copy commands into the build step.
3. Update the card link and status badge in [`index.html`](index.html).
