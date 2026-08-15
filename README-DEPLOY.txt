RUNNERS ERRANDS — DEPLOY THIS FOLDER (not a single file)
=========================================================

WHY THIS CHANGED
----------------
Previously the icon was embedded inside the HTML as a base64 data URI.
That works on desktop, but mobile browsers do NOT reliably accept data-URI
icons for bookmarks and home-screen shortcuts. When the browser can't find
a usable icon file, it auto-generates a placeholder from the first letter
of the site title — which is why "Runners Errands" showed as a plain "R".

The fix is real icon FILES at real URLs, plus a web manifest. That requires
deploying a folder rather than one HTML file.

HOW TO DEPLOY
-------------
1. Go to vercel.com/drop
2. Drag THIS ENTIRE FOLDER in (not just index.html)
3. Deploy

Vercel serves index.html at the root and the icon files alongside it,
which is exactly what mobile browsers need.

WHAT'S IN HERE
--------------
  index.html            the demo (unchanged apart from the icon links)
  favicon.ico           browser tab
  apple-touch-icon.png  180x180 — iOS bookmarks & home screen
  icon-192.png          Android Chrome
  icon-512.png          Android splash / high-DPI
  site.webmanifest      tells Android which icons to use
  alt-navy-icons/       optional alternative, see below

OPTIONAL — NAVY ICON INSTEAD OF WHITE
--------------------------------------
The default icons are the navy R on a white background, matching the logo
everywhere else. The alt-navy-icons/ folder has the reverse: a white R on
a navy background, which stands out more on a phone home screen.

To use them, copy the four files from alt-navy-icons/ into the main folder,
replacing the originals. Then delete alt-navy-icons/ before deploying.

AFTER DEPLOYING
---------------
Remove the old bookmark from your phone first, then re-add it. Mobile
browsers cache bookmark icons aggressively and will keep showing the old
one otherwise — this is the most common reason people think it didn't work.
