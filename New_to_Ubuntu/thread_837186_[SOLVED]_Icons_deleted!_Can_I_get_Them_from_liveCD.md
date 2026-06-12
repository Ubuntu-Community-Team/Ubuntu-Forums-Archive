---
title: "[SOLVED] Icons deleted! Can I get Them from liveCD?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by yragrelluf on 2008-06-22
I am big on free space, so I deleted some themes and icons, and only kept a few of my favorites. I was wondering if it is possible to boot from a liveCD and locate the icons, and copy them to a flash drive, sd card, or right to where they should be on the hard drive?, Because I regret deleting a few of them (gnome and gnome alternative) I think because of deleting them, the ubuntu icon, or alternatively the gnome foot icon are now missing from the applications menu.

---

### Post by sayakb on 2008-06-22
Ya.. sure you can. Boot into the LiveCD. From there, open Nautilus as superuser by typing into terminal:
```
gksudo nautilus
```
Then navigate to the LiveCDs /usr/share/icons folder and copy it to your installed Ubuntu's respective location..

---

### Post by sisco311 on 2008-06-22
Try to reinstall gnome-icon-theme from synaptic.

---

### Post by yragrelluf on 2008-06-22
I reinstalled gnome-icon-theme, and it worked perfectly! Thank you all for responding so fast. Im glad I didn't need to use the liveCD, but Im also glad that I could!:lolflag:

---

