# Apache Bro Motoworks — Website

Website for **Apache Bro Motoworks**, a multi-brand motorcycle service, modification, and wrap shop in Khatima, Uttarakhand. Servicing Royal Enfield, KTM, Bajaj, Yamaha, Kawasaki, Suzuki, and Honda — commuters to performance bikes.

A single self-contained `index.html` — no build step, no framework, no dependencies to install. Open it in a browser and it works.

## Stack

- Plain HTML, CSS, and vanilla JS in one file
- Google Fonts (Big Shoulders Display, Inter, JetBrains Mono) loaded via CDN
- No backend, no database, no npm/build tooling

## Project structure

```
index.html          the entire site
images/
  bike-modification.jpg   photo shown in the "Bike Modification" card
  bike-wrap.jpg            photo shown in the "Bike Wrap" card
```

If a photo isn't in the `images/` folder yet, that card shows a labeled placeholder instead of a broken image — safe to deploy either way.

## Running it locally

No install needed. Either:
- Double-click `index.html`, or
- Serve it with any static server, e.g. `python3 -m http.server` from this folder, then open `http://localhost:8000`

## Deploying

Free hosting via [Netlify](https://netlify.com), [Vercel](https://vercel.com), or [Cloudflare Pages](https://pages.cloudflare.com) all work the same way for a static file like this:

1. Drag the `index.html` file (and `images/` folder, if used) onto Netlify Drop for an instant test link: https://app.netlify.com/drop
2. For the real domain: create an account, deploy the same way, then add `apachebro.com` under Domain settings and follow the DNS instructions it gives you.
3. HTTPS is issued automatically once DNS points correctly — no extra steps.

## Editing content

Everything below is a plain text/attribute edit in `index.html` — no rebuild required, just save and re-upload.

### Contact info
Search for these in the Contact section:
- Address — inside the `Workshop Address` row
- Phone / WhatsApp — currently `+91 75055 91638`. The phone number appears in several places as `tel:+917505591638` (Call buttons) and `https://wa.me/917505591638` (WhatsApp buttons + the booking form). Update **all** occurrences if the number changes.
- Email — `mailto:apachebro@gmail.com`
- Hours — plain text in the `Opening Hours` row

### Social links
Search for `instagram.com`, `facebook.com`, and `youtube.com` — each appears in three spots (top social strip, hero follower pills, footer). Update all three together to keep them consistent.

Follower counts (hero section) are static text — search for `hf-count` and update the numbers by hand whenever they change. There's no live API wired up (that requires a paid service — see project notes if you want that added later).

### Google Maps
Search for `map-box` in the Contact section. The `<iframe src="...">` holds the embed link. To change the pinned location: open it in Google Maps → Share → Embed a map → copy the `src` URL → paste it in.

### Google Reviews
The "Leave A Review" button, the Google icon in the social strip, and the footer "Google Reviews" link are still placeholder (`href="#"`) until a real review link is added. Get one via the Business Profile's "Ask for reviews" option, then update all three.

### Services list
Search for `var services = [` in the `<script>` block — it's a plain JS array of `[name, description]` pairs that renders the whole service grid automatically. Add, remove, or reorder entries there; no HTML editing needed for the grid itself.

### Booking form → WhatsApp
The booking form doesn't use a backend. On submit, it builds a pre-filled WhatsApp message from the form fields and opens `wa.me` addressed to the garage's number — the customer taps Send once to deliver it. To change which number it goes to, search for `WHATSAPP_NUMBER` in the script and update it.

## Notes

- Mobile nav switches to a hamburger menu under 1000px width; a separate sticky action bar (Call / WhatsApp / Directions / Book) appears under 760px.
- All content is visible by default even if JavaScript fails to load — animations are progressive enhancement only, never load-bearing for visibility.
- No analytics, tracking, or third-party scripts beyond Google Fonts.
