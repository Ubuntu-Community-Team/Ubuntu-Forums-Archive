---
title: "Compile radeon with patch"
date: 2015-01-04
forum: Packaging and Compiling Programs
---

### Post by mcirillo on 2015-01-04
Due to some artifacting/display issues while watching video (in XBMC 14 kodi) with the current radeon driver I went on the hunt for alternatives. FGLRX doesn't seem to offer any improvement so I tried the xorg-edgers ppa. Those drivers, however, crash due to some recent cleanup (problem described more technically here: [https://bugs.freedesktop.org/show_bug.cgi?id=86837](https://bugs.freedesktop.org/show_bug.cgi?id=86837)). I'm attempting to compile mesa with a patch that supposedly fixes the crash (here: [http://patchwork.freedesktop.org/patch/39400/](http://patchwork.freedesktop.org/patch/39400/)).

I can get as far as cloning the repo, but from there I'm not sure which branch I should be on and the correct way to apply the patch afterward. Any guidance would be appreciated!

Hardware is an AMD 5350 APU, kernel 3.13.0-43 generic

---

### Post by mcirillo on 2015-02-13
Fixed in mesa 1.5/6 - [https://bugs.freedesktop.org/show_bug.cgi?id=86837](https://bugs.freedesktop.org/show_bug.cgi?id=86837)

---

