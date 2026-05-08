# Ikda Originals

Public-domain original books for the Ikda (읽다) language-learning app.

## Structure

```
index.json              # Registry: slug, file, bytes, chapter count, title, level
books/{slug}.json       # One book per file: array of ReadingPassage chapters
```

## How the app uses these files

The Ikda app fetches per-book files on demand via the jsDelivr CDN:

```
https://cdn.jsdelivr.net/gh/ykmaeng/ikda-originals@master/index.json
https://cdn.jsdelivr.net/gh/ykmaeng/ikda-originals@master/books/{slug}.json
```

Each book is downloaded once, cached locally (IndexedDB), and read offline thereafter.

## Why this lives in a separate repo

The Ikda app's main repo is private (commercial code). Original book content is
public-domain (Project Gutenberg etc.) and is split out so it can be served from
a public CDN without exposing private source.

## Adding / updating books

In the main app repo:

```sh
node scripts/convert-originals-to-json.mjs   # TS → JSON conversion
pnpm publish:originals                        # sync + commit + push
```

## License

All book content is in the public domain (Project Gutenberg, Wikisource, etc.).
This repository is published under the same terms as the original sources.
