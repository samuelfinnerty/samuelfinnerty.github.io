# samuelfinnerty.github.io

Source for Samuel Finnerty's academic website, built with [Quarto](https://quarto.org) and published to GitHub Pages by GitHub Actions.

Every commit to `main` rebuilds and republishes the site, usually within two minutes. You can edit everything in the browser on GitHub; RStudio is optional.

## Making changes

| To change | Edit |
|---|---|
| Home page text | `index.qmd` |
| Publications (Publications page and home page) | `data/publications.yml` |
| Talks list | `data/talks.yml` |
| Media, podcasts, workshops, photos | `talks.qmd` |
| Writing and commentary | `writing.qmd` |
| Teaching | `teaching.qmd` |
| Approach | `approach.qmd` |
| CV | Replace `cv/Samuel-Finnerty-CV.docx` (keep the file name) |
| Menu, footer, site description | `_quarto.yml` |
| Colours and typography | `_theme/` |

**Editing in the browser:** open the file on GitHub, click the pencil icon, make the change, then click *Commit changes*. Check progress under the *Actions* tab; a green tick means the site is live.

**Adding a publication:** in `data/publications.yml`, copy an existing entry, paste it at the top of its group, and edit the fields. Set `featured: true` to show it on the home page.

**Adding a photo:** upload it to `assets/images/` (ideally under 1 MB and no wider than 1600 px), then add a line in the `gallery` block of `talks.qmd`.

**CV:** upload a new `Samuel-Finnerty-CV.docx` to the `cv` folder. The build converts it to PDF with LibreOffice. Check the PDF once after the first build: fonts that are not installed on the build server (e.g. Aptos) are substituted, which can shift the layout. If it looks wrong, export the PDF from Word yourself, upload it as `cv/Samuel-Finnerty-CV.pdf`, and delete the `.docx`.

## Previewing locally (optional)

Open `samuelfinnerty.github.io.Rproj` in RStudio and click *Render* on any page, or run `quarto preview` in a terminal. The built site goes to `_site/`, which is not committed.

## Automatic checks

- **Publish site** (`.github/workflows/publish.yml`): builds and publishes on every commit.
- **Check links** (`.github/workflows/check-links.yml`): checks every link after each publish and on the 1st of each month. Broken links appear in the run summary under *Actions*. LinkedIn links are skipped because LinkedIn blocks automated checks.

## Warming stripes

The stripes are drawn from NASA GISTEMP global annual temperature anomalies in `data/gistemp-annual.csv`, following Ed Hawkins' warming-stripes design. To add a new year, append a row to the CSV and commit; the build regenerates the graphic. Update the year range in the caption in `index.qmd` and the footer in `_quarto.yml`.

## Custom domain

1. Buy the domain from a registrar (e.g. Cloudflare, Porkbun, Namecheap).
2. In the registrar's DNS settings, add:
   - four `A` records for the bare domain (`@`) pointing to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - a `CNAME` record for `www` pointing to `samuelfinnerty.github.io`
3. On GitHub: *Settings → Pages → Custom domain*, enter the domain, save, and tick *Enforce HTTPS* once it becomes available (can take up to a day).
4. In `_quarto.yml`, change `site-url` to the new address.

The old `samuelfinnerty.github.io` address will redirect automatically.

## Licence

The repository is released under CC0 (see `LICENSE`). Fonts (Literata, Hanken Grotesk) are under the SIL Open Font License; see `assets/fonts/`.
