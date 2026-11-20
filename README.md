# Drawing Tel Aviv

An interactive map of my drawings of Tel Aviv. Each drawing is pinned to the place it was drawn.

This is a plain static site: HTML, CSS and JavaScript, with no build step and no dependencies to install. It runs as-is on GitHub Pages.

## Folders

| Folder | What's in it |
| --- | --- |
| `drawings/` | The drawing images (JPG, PNG or WebP). |
| `data/` | Location data. `drawings.json` lists every drawing and where it was made. |
| `site/` | The public map that visitors see. |
| `tagger/` | A tool for me to place drawings on the map and write their entries in `data/drawings.json`. Not linked from the public site. |

The root `index.html` just redirects to `site/`.

## Data format

`data/drawings.json` is an array with one entry per drawing:

```json
[
  {
    "file": "rothschild-blvd-01.jpg",
    "title": "Rothschild Boulevard",
    "lat": 32.0636,
    "lng": 34.7745,
    "date": "2026-05-14",
    "notes": "Morning, under the ficus trees"
  }
]
```

`file` is a filename inside `drawings/`. Only `file`, `lat` and `lng` are required.

## Running locally

Browsers block `fetch` from `file://` pages, so serve the repo root over HTTP:

```sh
python3 -m http.server
```

Then open http://localhost:8000/site/ (map) or http://localhost:8000/tagger/ (tagger).

## Publishing on GitHub Pages

In the repo's Settings → Pages, deploy from the default branch, root folder (`/`). The map will be at `https://<user>.github.io/drawing-tel-aviv/`. Serving from the root (not `/site`) matters because the map loads `../data/` and `../drawings/`.

The empty `.nojekyll` file tells GitHub Pages to serve the files as they are, without running Jekyll.
