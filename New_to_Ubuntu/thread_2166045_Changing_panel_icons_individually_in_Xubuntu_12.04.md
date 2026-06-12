---
title: "Changing panel icons individually in Xubuntu 12.04"
date: 2013-08-07
forum: New to Ubuntu
---

### Post by marinecomm on 2013-08-07
I'm running Xubuntu 12.04 64-bit and I was wondering if there was any way to change the icons in the top panel individually instead of selecting an icon theme in the Appearance settings?

---

### Post by Dennis N on 2013-08-07
This is certainly possible. Locate the current icon theme in /usr/share/icons/ and then find in the theme's subfolders the offending icons in question. Each icon comes in a set of sizes stored in more subfolders: 16, 22, 24, 32, 48, 64, 96 (numbers refer to pixel size) and scalable. In general, you need to replace each icon size that is in use. Suggest you rename the originals with .bak so you can revert.

Your replacements should be of the same size as the originals they replace, of course.

If you can't see the icons you want to fix under /usr/share/icons/, also check /usr/share/pixmaps.

---

### Post by marinecomm on 2013-08-07
OK, sounds simple enough. I'll do that. Thank you very much

---

