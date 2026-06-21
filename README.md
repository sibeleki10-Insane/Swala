# Swala

Namibia's vacancies, tenders, and youth & community development opportunities — gathered from official sources, in one place.

Swala is made possible by **Spacecode Solutions**, for the people of Namibia.

## What it is

A single-page, magazine-style site (`index.html`) listing current opportunities in three categories:

- **Vacancies** — every national government ministry, the Office of the President/Vice-President/Prime Minister/Attorney-General, all 14 regional councils, and 13 major town/municipal councils
- **Tenders** — procurement notices from the Central Procurement Board of Namibia, e-Procurement, and individual ministries
- **Youth & Community Development** — funding, training and coordination programmes for Namibian youth

Visitors can filter by category, field/sector, qualification, and experience level, or search by keyword. Each listing shows its publication date and closing/due date where the issuing institution has published one, and links straight through to the official source.

Every card uses a stock photograph (not icons) representative of its field, sourced from Unsplash.

### Live deadline behaviour

- Listings carry an optional `dueAt` ISO timestamp. Once that moment passes, the listing is automatically dropped from the page (re-checked every 60 seconds while the page is open).
- Listings carry an optional `publishedAt` ISO timestamp. For the first 10 hours after that moment, the card glows **faint green** ("New"). After 10 hours it settles to the standard **gold** glow.
- In a listing's final 10 hours before `dueAt`, the card glows **red** ("Closing soon") with a soft pulse.
- Listings without a known specific date (most standing ministry/council notice-board pages) show the standard gold state and never auto-drop — no fabricated urgency is added where the source didn't publish one.

## Sources

All listings link only to primary official sources: `.gov.na` ministry/agency/council sites, `.org.na`/`.com.na` municipal sites, the Central Procurement Board of Namibia (cpbn.com.na), the national e-Procurement portal, and named statutory bodies (e.g. NamRA, NYS, EIF). No unofficial scraper or aggregator job sites are used.

## Contact

A contact form at the bottom of the page (before the footer) opens the visitor's email client via a `mailto:` link addressed to `spacecode.solutions@outlook.com` with "Swala" in the subject line — no backend or third-party service required.

## Tech

Plain HTML/CSS/JS — no build step, no dependencies (one CDN: Unsplash-hosted images). Open `index.html` in any browser, or serve the folder with any static file host (GitHub Pages, Netlify, etc.).

## Updating listings

Edit the `data` array near the top of the `<script>` block in `index.html`. Each entry follows this shape:

```js
{cat:"vacancy"|"tender"|"youth", photo:"<PHOTO key>", title, org, field, qualification, experience,
 published, due, publishedAt:"<ISO datetime or null>", dueAt:"<ISO datetime or null>", desc, url}
```

`photo` must be one of the keys in the `PHOTO` map (office, meeting, construction, finance, health, agri, edu, ict, youth, handshake). Use `"Not specified"` for any display date/field the official source doesn't state — don't guess. Only set `publishedAt`/`dueAt` when the issuing institution published a genuine specific date.

## Disclaimer

Information is compiled from public sources and may change after publication. Always verify directly with the issuing institution before applying, bidding, or signing anything.

---

© 2026 Swala. Built by Spacecode Solutions.
