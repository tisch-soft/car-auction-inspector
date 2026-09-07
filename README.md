# Insurance Lots

The public landing page for a daily list of insurer-sold cars on Copart:
lots that run and drive, on a repairable title, with keys, under 60,000 miles
and 2022 or newer.

**https://tisch-soft.github.io/car-auction-inspector/**

## What is in this repository

| Path | What it is |
|---|---|
| `index.html` | The landing page. **Generated — do not edit by hand.** |
| `.nojekyll` | Tells Pages to serve the files as they are, with no Jekyll build step. |

## How it is published

Pages serves this repository directly: **Settings → Pages → Source: Deploy from
a branch → main → /(root)**. No Actions workflow and no build step — the page is
plain static HTML, so the branch is the site.

An earlier attempt used an Actions workflow with `actions/configure-pages` and
`enablement: true`. It could not switch Pages on: the workflow token is refused
unless the repository already grants Actions write permission, and a job that
declares the `github-pages` environment fails before its first step when Pages
has never been enabled. Branch deployment avoids both problems.

## How it is built

`index.html` comes from `tools/build-site.js` in the private project repo,
which reads that night's classified data. Regenerate and publish with:

    node tools/build-site.js        # writes site/index.html
    node tools/nightly.js --publish # rebuild everything, then commit and push

Only the teaser is published here. The full list, every filter and the
night-to-night history are the paid product and never enter this repository —
neither do the raw dumps, which are Copart's data rather than ours to
redistribute.

## The checkout link

The "Get the full list" button points at a placeholder until the store exists.
Change `CHECKOUT_URL` at the top of `tools/build-site.js` and rerun.

---

Not affiliated with Copart, Inc.
