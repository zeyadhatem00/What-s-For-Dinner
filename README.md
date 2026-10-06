# What's For Dinner

A static recipe-discovery page that presents a randomly selected meal with its ingredients, cooking instructions, nutrition summary, and chef's tips. The page is designed as a responsive, single-screen experience: choose another recipe with the **Try Another Recipe** button or move between the detail tabs.

## Features

- Randomly selects one of the 15 recipe records embedded in the browser-side application on initial load and when **Try Another Recipe** is clicked.
- Shows recipe imagery, rating/review text, preparation and cooking times, servings, difficulty, and cuisine/type labels.
- Organizes each recipe into **Ingredients**, **Instructions**, **Nutrition**, and **Chef's Tips** tabs.
- Displays extended-preparation messaging for recipes marked with the corresponding data flag.
- Uses a responsive Bootstrap layout with local image, icon, stylesheet, and font assets.

> Recipe content, ratings, nutrition values, and tips are static data in `js/main.js`; this project does not fetch recipes or calculate nutrition at runtime.

## Tech stack

- Semantic HTML in [`index.html`](index.html)
- Vanilla JavaScript and template-string rendering in [`js/main.js`](js/main.js)
- Bootstrap styles and components from the bundled [`css/bootstrap.min.css`](css/bootstrap.min.css) and [`js/bootstrap.bundle.min.js`](js/bootstrap.bundle.min.js)
- Font Awesome styles and webfonts bundled in [`css/all.min.css`](css/all.min.css) and [`webfonts/`](webfonts/)
- Custom responsive styling in [`css/style.css`](css/style.css) and [`css/media.css`](css/media.css)

There is no package manifest, build configuration, dependency installation step, or environment-variable file in this repository. The browser and a local static file server are sufficient.

## Run locally

1. Clone the repository and enter its root directory:

   ```bash
   git clone https://github.com/zeyadhatem00/What-s-For-Dinner.git
   cd What-s-For-Dinner
   ```

2. Start a static HTTP server from the repository root. For example, with Python 3:

   ```bash
   python3 -m http.server 8000
   ```

3. Open [http://localhost:8000](http://localhost:8000) in a browser. Stop the server with `Ctrl+C`.

Opening `index.html` directly may work in a modern browser, but serving the repository over HTTP keeps relative asset loading consistent.

## How it works

- `index.html` supplies the navigation shell and an empty `#row` mount point.
- `js/main.js` stores the recipe records, selects a random index, and renders the complete recipe card into `#row`.
- Bootstrap's bundled JavaScript powers the recipe detail tabs and the responsive navigation collapse.
- The **Try Another Recipe** button calls `changerecepie()`, which replaces the rendered card with another randomly selected record.
- CSS and image paths are relative to the repository root, so keep the existing directory layout when serving or publishing the site.

## Repository layout

| Path | Purpose |
| --- | --- |
| [`index.html`](index.html) | Page shell, navigation, and script/style references |
| [`js/main.js`](js/main.js) | Embedded recipe data, random selection, and HTML rendering |
| [`css/style.css`](css/style.css) | Main visual styles for the recipe card and detail panels |
| [`css/media.css`](css/media.css) | Responsive rules for narrower screens |
| [`images/`](images/) | Recipe, avatar, and favicon image assets |
| [`webfonts/`](webfonts/) | Bundled Font Awesome webfont files |
| [`.github/workflows/static.yml`](.github/workflows/static.yml) | GitHub Pages deployment workflow for pushes to `main` or manual dispatch |

## Development notes and current boundaries

- To add or revise a recipe, edit the `allRecpies` array in [`js/main.js`](js/main.js), including its image path and detail fields.
- The page has no backend, database, authentication, API integration, or client-side persistence. Recipe changes are source changes and require republishing the static files.
- Header controls for **Saved Recipes**, **Recent**, **Settings**, and **Profile**, along with the recipe-card bookmark/share buttons, are currently visual controls; no corresponding event handlers or persistence are implemented in `js/main.js`.
- The repository contains a GitHub Actions workflow that uploads the repository as a Pages artifact, but no live deployment URL is documented here or assumed by this README.
