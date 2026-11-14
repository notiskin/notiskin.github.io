# Notiskin docs

The docs site for [Notiskin](https://github.com/notiskin/notiskin), published at **https://notiskin.github.io/**: how to make themes and plugins, every variable, the `notiskin` object, settings, developer mode, and how publishing and review work.

Plain HTML in [`site/`](site/), no generator. `site/style.css` uses the same color tokens as the app (`src/gui/brand.css`), and the Fraunces and Inter fonts (SIL OFL, licenses next to them) are bundled.

## Keeping it true to the app

The app is in another repository, so [`test/site.test.js`](test/site.test.js) checks these pages against the app's code: every `--ns-*` variable, every `window.notiskin` method, the marketplace rules, the color tokens, working links, and that the example themes pass the marketplace check and the example plugin settings parse. CI checks out `notiskin/notiskin`, builds it, and runs the test on every push and pull request, and once a week so a change in the app that the docs haven't caught up with shows up here.

To run it yourself:

```bash
git clone https://github.com/notiskin/notiskin ../notiskin
(cd ../notiskin && npm ci && npm run build)
NOTISKIN_APP_DIR=../notiskin npm test
```

When the app gets a new variable or a new `notiskin` method, the test fails here until the page documents it.

## Publishing

A push to `main` that touches `site/` is published by `.github/workflows/pages.yml` (Settings → Pages → Source must be "GitHub Actions"). The old address `https://notiskin.github.io/notiskin/` is a redirect page kept in the app repository, because releases 0.7 to 0.10.2 still link to it. Newer releases open this site.

MIT licensed, like the app.
