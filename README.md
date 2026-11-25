# GATE CS 2027 — Pattern Study Guide (installable PWA)

An offline-capable study app: weightage pie chart → subject → topic → notes, PYQs and predicted questions,
plus interactive labs and a 60-day plan. No server, build step or internet connection is needed after the first load.

## Files
| File | Purpose |
|---|---|
| `index.html` | The whole app (notes, PYQ data, simulators) in one file |
| `manifest.json` | Name, colours and icons so browsers can install it |
| `sw.js` | Service worker: caches everything so the app works offline |
| `icon-192.png`, `icon-512.png`, `maskable-512.png` | Install icons |
| `apple-touch-icon.png`, `favicon-32.png` | Apple touch icon and favicon |

## Try it on your computer
A service worker only runs over **http://localhost** or **https://** (not by double-clicking the file).

    cd gate-cs-pwa
    python3 -m http.server 8000
    # open http://localhost:8000 in Chrome or Edge

(Double-clicking `index.html` still works as a normal web page; it just can't be installed or cached.)

## Put it on your phone
1. Upload the **contents of this folder** to any free static host that gives you HTTPS —
   GitHub Pages, Netlify (drag-and-drop), Cloudflare Pages or Vercel. Keep the files in the same folder structure.
2. Open the link on your phone.
   * **Android / Chrome:** tap **Install as an app** in the banner at the top (or the browser menu → *Install app*).
   * **iPhone / Safari:** Share → **Add to Home Screen**.
   * **Desktop Chrome / Edge:** click the install icon in the address bar.
3. Open it once while online; after that it works with no connection.

## Updating
The cache name (the `CACHE` constant in `sw.js`) contains a hash of `index.html` (`gate-cs-494c83f829`). If you edit `index.html` by hand, change
that suffix to any new text so installed copies refresh straight away (the old cache is then deleted automatically). Even without that, the app refreshes its cache in the background and shows the new version the next time you open it.

## Your data
"Mark solved" ticks are saved in your browser's local storage on that device (they do not sync between devices
and are cleared if you clear the site's data).
