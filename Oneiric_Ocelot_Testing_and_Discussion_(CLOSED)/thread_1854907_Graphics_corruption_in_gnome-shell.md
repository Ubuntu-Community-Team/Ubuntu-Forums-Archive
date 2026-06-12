---
title: "Graphics corruption in gnome-shell"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by supernaut on 2011-10-05
My problem is that when I launch gnome-shell after installing the proprietary fglrx drivers, the global menu from Unity appears and a bunch of characters are missing on screen.

I don't really need the proprietary drivers, I only installed them because gnome-shell was working fine under what I assume were the Gallium drivers except for a tiny bit of corruption that I thought the proprietary drivers might fix.

However, now it seems I'm completely stuffed as I can't figure out how to return to the Gallium drivers, stuck in either VESA or useless fglrx. Whatever happened to editing Xorg.conf?

---

### Post by dino99 on 2011-10-05
purge all the installed graphic drivers, then reinstall fglrx

sudo rm /etc/X11/xorg.conf
gnome-shell --replace

---

### Post by distobj on 2011-10-06
I have the same problem. It's a known bug;

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/838577)

---

### Post by P-I H on 2011-10-07
I have installed Catalyst 11.9, fglrx, by use of the method described on cchtlm.com and the upper panel in GS looks OK.
Some fonts are however not displayed correctly, for example if you position the mouse over an item with a help text.

---

