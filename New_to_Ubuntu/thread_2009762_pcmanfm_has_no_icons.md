---
title: "pcmanfm has no icons?"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by neil_1 on 2012-06-24
pcmanfm on a minimal install of ubuntu doesn't have any icons.
anyone know if i have to install something beforehand ?

i've tried this option but it didn't work:
[http://ubuntuforums.org/showpost.php?p=11312045&postcount=4](http://ubuntuforums.org/showpost.php?p=11312045&postcount=4)

edit:
what i've installed :
xorg, slim, openbox, pcmanfm and the oxygen and tango icons

---

### Post by Irihapeti on 2012-06-25
The file in question needs to be named .gtkrc-2.0 (not .gtkrc.mine as in the linked post).

Rename the file, log out and in again, and you should see the icons.

---

