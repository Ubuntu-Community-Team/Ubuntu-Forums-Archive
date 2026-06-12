---
title: "Item in menu but not in alacarte"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-06-11
Hi All,
I have installed POV-Ray in wine and it works great. There was a desktop icon but no menu icon, so I thought I would create one.
I did so, but Imucked it up somehow. Anyway, I can see on my menu in the wine menu is the Povray icon.
But the problem is when I open alacarte to edit the item, its not there. There is no trace of the icon i have created, yet it is in the menu.

Is there a config file that I can edit to remedy this?

Oh yeah, im using classic gnome menu, not Unity.

---

### Post by Senior_Buckethead on 2012-06-15
Bump

---

### Post by SDX0 on 2012-06-15
In Xubuntu the .desktop files used for the menu are in ~/.local/share/applications and /usr/share/applications

I'm not sure if the same applies to Gnome, but you could see if your menu entry is hidden in one of them.

---

