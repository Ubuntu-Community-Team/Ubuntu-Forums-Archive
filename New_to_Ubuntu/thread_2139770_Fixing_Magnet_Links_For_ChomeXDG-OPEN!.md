---
title: "Fixing Magnet Links For Chome/XDG-OPEN!"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by SukuC23101993 on 2013-04-27
Hey, I done a fresh install of 13.04 but now my magnet links won't work! I've literally done everything I did last time but for some reason it won't work. I followed [this]("http://www.foresightlinux.se/make-chromium-to-open-magnet-links/") guide last time but for some reason it won't work now. I've tried it several times and even on a different system but it still won't work. Enlighten me guys!

---

### Post by SukuC23101993 on 2013-04-28
Sorry for bumping but this is so annoying!

---

### Post by TheDescartes on 2013-05-31
This is a reported bug on Launchpad, a problem with xdg-open. Turns out this is not the first time the bug has occurred either.
I fixed it by adding the lines shown here [http://www.void.gr/kargig/blog/2012/01/24/open-magnet-urls-with-xdg-open/](http://www.void.gr/kargig/blog/2012/01/24/open-magnet-urls-with-xdg-open/) to xdg-open (around line 448).
For me, it was as easy as opening SCiTE (or editor of your choice) with sudo from the terminal, then opening xdg-open from within SCiTE. Then, I made my edits and saved. Now Transmission opens magnet links for me!
Note the name of Transmission in /usr/bin also. Mine was named Transmission-gtk.

---

