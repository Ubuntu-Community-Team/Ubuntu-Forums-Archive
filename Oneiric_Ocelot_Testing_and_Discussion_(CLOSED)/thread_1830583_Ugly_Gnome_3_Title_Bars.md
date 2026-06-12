---
title: "Ugly Gnome 3 Title Bars"
date: 2011-08-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Mars11 on 2011-08-21
I've followed the instructions on how to fix this, but none of them work. I'm running Ubuntu 11.10 Alpha 3, which my be part of the reason. The nice looking title bars do show up when using Unity though. Any ideas on how to fix it?

---

### Post by Mars11 on 2011-08-22
I just noticed that when I remove gnome-accessibility-themes it uninstalls gnome-themes-standard and when I install gnome-themes-standard it installs gnome-accessibility-themes. I think that might explain my issue. Does anyone know how I could only install one?

---

### Post by overdrank on 2011-08-22
Moved to Ubuntu +1 (Oneiric Ocelot)

---

### Post by Harry33 on 2011-08-22
The new gnome-themes-standard depends on gnome-accessibility-themes.
So they need to be both installed.

The issue of broken window decorations and theming is due to the fact that the old mutter and clutter packages of Oneiric repos are not compatible with new themes.

You have two choices:

1) downgrade the gnome-themes-standard
2) install newer mutter and clutter from ricotz testing PPA

This issue has already been dealt with in another thread here.
[http://ubuntuforums.org/showthread.php?t=1828162](http://ubuntuforums.org/showthread.php?t=1828162)

---

### Post by Mars11 on 2011-08-22
Thanks, I'll check it out.

---

