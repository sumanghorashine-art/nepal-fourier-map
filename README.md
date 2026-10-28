# Nepal from Fourier circles

An animated map of Nepal drawn by a chain of 7,000 rotating circles (epicycles). When the loop closes, the map fills crimson with a blue border, and the moon and sun from the national flag appear inside it.

Any closed outline can be written as a Fourier series:

```
x(t) = x0 + Σ (a_k cos kt + b_k sin kt)
y(t) = y0 + Σ (c_k cos kt + d_k sin kt)
```

`scripts/build.py` resamples the border evenly, runs an FFT, keeps the 7,000 strongest terms and embeds them in `index.html`. The page is static and has no dependencies.

## Run

Open `index.html` in a browser. To rebuild after changing `template.html` or the border data:

```bash
pip install numpy
python scripts/build.py
```

## Deploy

Push to `main`. In *Settings → Pages* set the source to **GitHub Actions**; `.github/workflows/pages.yml` publishes the site.

## Data

Border: Natural Earth 10m admin-0 (public domain), via `datasets/geo-countries`. It has 1,021 points for Nepal and does not show the Kalapani–Lipulekh–Limpiyadhura area as Nepal's.

## License

MIT

## Anthem audio

`assets/anthem.mp3` is embedded into `index.html` at build time as a base64 data URI, so the page is a single self-contained file. The drawing follows the playback position, so the map finishes exactly when the song ends. The Replay / Circles / Speed controls are hidden in the page (`<div class="row" hidden>` in `template.html`). Use a recording you have the right to publish; check the licence before committing it.
