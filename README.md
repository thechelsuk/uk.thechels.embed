# uk.thechels.embed

A single static page that wraps a YouTube embed, served at `https://embed.thechels.uk`.

## Why

YouTube now refuses embeds that arrive without an HTTP referrer, showing *"Video player configuration error — Error 153"*. Apps such as NetNewsWire render articles from a local base URL, so iframes in their themes send no referrer.

Embedding this page instead means YouTube sees `embed.thechels.uk` as the referrer and the video plays.

## Usage

```text
https://embed.thechels.uk/?v={VIDEO_ID}
```

- `v` must be an 11-character YouTube video ID; anything else is rejected.
- Without a valid ID, the page shows a short note and a footer explaining what it's for. The footer is removed before the player loads, so embeds fill the frame as before.
- The video is embedded from `youtube-nocookie.com`.
- Once loaded, the page posts `{ type: "thechels-embed-ready", videoId }` to its parent so the embedding page can fall back if it never arrives.

Used by the [NetNewsWire themes](https://github.com/thechelsuk/uk.thechels.themes.nnw).

## Privacy

Static page on GitHub Pages: no analytics, cookies, storage or server-side code.

## Hosting

- GitHub Pages from `main` at the repository root.
- `CNAME` sets the custom domain `embed.thechels.uk`.
- DNS: `embed` CNAME → `thechelsuk.github.io` (DNS only, not proxied).
