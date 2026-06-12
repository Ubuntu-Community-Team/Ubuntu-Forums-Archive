---
title: "Wine - Where is the fake Windows C: Drive?"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by Loerie on 2012-12-13
[B]

I installed a program under wine from a CD. The installation defaulted to an elusive C drive. Where do I find the installed program, where do I find the C drive?

I also tried to install it to the Ubuntu file system, which is drive Z in the installation drop-down, but it doesn't allow me to do that.

[/B]

---

### Post by deadflowr on 2012-12-13
Wine creates a hidden folder inside your home folder.
To find it open home folder and either press ctrl + h, or go to the menu and enable hidden folders.
The folder will be listed with a dot, like .wine.

---

### Post by oldos2er on 2012-12-13
~/.wine/drive_c/

The "." in front of "wine" means it's a hidden folder. Use Ctrl-h in Nautilus to see all hidden files and folders.

---

### Post by TheFu on 2012-12-13
> **Loerie said:**
> [B]

I installed a program under wine from a CD. The installation defaulted to an elusive C drive. Where do I find the installed program, where do I find the C drive?[/B]

It is here: **~/.wine/drive_c/**
or
$HOME/.wine/drive_c/
These are the same place.

However, there should be a menu item with Wine --> Programs -- {whatever you installed} that will start the installed programs.  Use LXDE and it is under the main menu at the same level as Accessories, Games, Graphics, Internet ...   very easy to find.

---

