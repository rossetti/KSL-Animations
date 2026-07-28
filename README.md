<div align="center">
  <img src="assets/branding/ksl-logo.svg" alt="KSL — Kotlin Simulation Library" width="380">
</div>

# KSL Animations

The published gallery of KSL simulation animations, served by GitHub Pages at
**https://rossetti.github.io/KSL-Animations/**

Every animation here is a real run of a real model from the
[Kotlin Simulation Library](https://github.com/rossetti/KSL), captured to a trace and replayed in your
browser. Nothing is a recording: the player is reading the same trace file the desktop animation
application reads, through the same renderer, so what you see here is what the application shows.

## Why this is a separate repository

The site is generated, and generated artifacts do not belong in the history of a library. Keeping it apart
also means GitHub Pages can serve from the root of `main` without any of that affecting `rossetti/KSL`.

## What is generated and what is written

Most of this repository is produced by a build task and should never be edited by hand — the next build
discards the edit. The exceptions are the pages a person actually wrote.

| Path | |
|---|---|
| `index.html`, `gallery.html`, `assets/site.css` | written by hand |
| `catalog.toml` | written by hand — the blurb and "what to watch for" per animation |
| `a/*.html`, `animations.json`, `traces/`, `assets/posters/`, `assets/ksl-animation.js` | **generated** |

## Rebuilding

From a [KSL](https://github.com/rossetti/KSL) checkout beside this one:

```bash
./gradlew -p KSLAnimationCore jsBrowserProductionWebpack
```

```bash
./gradlew buildAnimationSite -Pout=../KSL-Animations
```

Then review the diff here, commit and push. The site is rebuilt when the animations change, which in
practice means alongside a KSL suite release rather than on a cadence of its own.

## License

GPL-3.0, the same as KSL itself — see [LICENSE.txt](LICENSE.txt). That covers the animation player
(`assets/ksl-animation.js`) shipped here, which is compiled from KSL sources.
