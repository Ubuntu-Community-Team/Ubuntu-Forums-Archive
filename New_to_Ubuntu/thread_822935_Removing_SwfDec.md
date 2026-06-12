---
title: "Removing SwfDec"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by gatorbowls on 2008-06-08
I installed Swfdec on Firefox for flash, but id just like to install the adobe flash..how do i uninstall Swfdec

---

### Post by quelx on 2008-06-08
**System** > **Administration** > **Synaptic**

search for **swfdec-mozilla** > right click > **Mark for Complete Removal** > **Apply**

---

### Post by jema on 2008-11-10
When I do that, it wants to remove gnome :confused:

---

### Post by gandaran on 2008-11-10
swfdec is a dependency of gnome-desktop-environment, this package is not needed, it was your choice installing it, if you want to keep it go to firefox » tools » addons » plugins right click the swfdec flash plugin and disable it, now firefox will use another flash plugin if it's installed

---

### Post by bolhuisbe on 2009-03-27
> **gandaran said:**
> swfdec is a dependency of gnome-desktop-environment, this package is not needed, it was your choice installing it, if you want to keep it go to firefox » tools » addons » plugins right click the swfdec flash plugin and disable it, now firefox will use another flash plugin if it's installed

in my case swfdec-mozilla came installed and enabled by default in lenny-amd64. so do i opt to remove "gnome" when i uninstall it in Synaptic? i'm trying to install the Adobe 10 flash plugin (test?)

---

### Post by bolhuisbe on 2009-03-27
crap, i just remembered i'd just jerry-rigged the stable i386 Adobe 10 player, ... that was before i found the amd64 test version :confused:

I AM A STUPID NEWBIE!!! lol

---

### Post by bolhuisbe on 2009-03-27
... alright, i safely removed the swf-mozilla plugin (even clicked "ok" when it prompted to remove "gnome"), was still having a problem.  effed up fixing that (accidentally ran "autoremove" on the just about everything), so i said screw it.

wiped the slate clean, started with a fresh install of Debian "lenny" amd64, re-removed the swf-mozilla plugin and installed affiliates, Synaptic-ed the debian-multimedia-keys package, added deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) lenny main to my sources list (made sure that "contrib" and "nonfree" sources were selected in the main window just in case), and Synaptic-ed flashplugin-mozilla.

i feel like i felt when i first started learning "the OS that must not be named", but it worked like a charm! :)

I AM A STUPID NEWBIE!!! lol

---

