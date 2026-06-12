---
title: "[SOLVED] install msttcorefonts w/o switching to them"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-05-13
so im trying to make safari run in ubuntu (just because) and i found this link
[http://www.myscienceisbetter.info/2008/02/installing-safari-3-beta-on-ubuntu.html]("http://www.myscienceisbetter.info/2008/02/installing-safari-3-beta-on-ubuntu.html")

step 3 and 4 say to download the msttcorefonts and then copy the files to the virtual C: (wine)

would it be possible for me to just install the fonts and mv the files rather than cp without screwing anything up?

the reason i would want to mv them rather than cp is so i can keep my default ubuntu fonts (i actually like them)

so basically is there any way i can get them to my WINE C: without changing any of my ubuntu fonts?

---

### Post by dizee on 2008-05-13
Yeah that should work. Ubuntu looks for fonts to load in /usr/share/fonts and .fonts in your home folder, so if you move them to the wine file, they'll load in Wine but not Ubuntu.

```
sudo mv /usr/share/fonts/truetype/msttcorefonts/{Arial,Times_New_Roman}*.ttf ~/.wine/drive_c/windows/fonts/
``` should do it.

---

### Post by tjwoosta on 2008-05-13
awesome, thanks

---

