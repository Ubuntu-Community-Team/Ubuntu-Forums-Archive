---
title: "X config is hosed"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by chlorox on 2011-09-16
I attempted to enable the proprietary driver for my ATI/Intel hybrid card. (HP Pavillion laptop). After rebooting, I attempted to login. I got a "failed to load Gnome session" error. I knew that these hybrid cards were poorly supported on Linux, so I'd love to go back to just using the Intel card. 

The problem is, normally I'd just delete the xorg.conf file and reboot.... but there IS no xorg.conf file anywhere on the system!

How do I get back to "the way things were"?

-Jim

---

### Post by Harry33 on 2011-09-16
> **chlorox said:**
> I attempted to enable the proprietary driver for my ATI/Intel hybrid card. (HP Pavillion laptop). After rebooting, I attempted to login. I got a "failed to load Gnome session" error. I knew that these hybrid cards were poorly supported on Linux, so I'd love to go back to just using the Intel card. 

The problem is, normally I'd just delete the xorg.conf file and reboot.... but there IS no xorg.conf file anywhere on the system!

How do I get back to "the way things were"?

-Jim

First, unable the ATI proprietary drivers exactly the way you enabled them in the first place, just reverse. Then check if you have fglrx and fglrx-amdcccle installed, uninstall both of them. After that check that you have the Intel or ATI open source drivers installed (xserver-xorg-video-ati / xserver-xorg-video-intel), install them.
Lastly, if you have the file /etc/X11/xorg.conf, remove it.

---

### Post by chlorox on 2011-09-16
I followed your advice, but OpenGL will no longer function.... hence no Gnome 3 or Unity. Unity 2D does work. This system is MORE than capable of running OpenGL. How do I get that functionality back for the Intel card? I seem to remember there being a few different packaages, a Mesa package or something...

---

### Post by chlorox on 2011-09-16
To answer my own question:

After installing a proprietary driver, Ubuntu updates alternatives. That means that it attempts to point to those drivers for 3D support EVEN after apt-get removing them. One could either, manually run update alternatives, or just force a re-install of the libgl1-mesa-glx package. That will do all the magic for you.

*Just putting this out there for all the boneheads like me that should know better*

---

### Post by Rocksinboxes on 2011-09-16
I've been having nothing but problems with FGLRX. The way I did to get them semi-functional, was to do a 'aticonfig --initial -f" . Gnome-Shell still doesn't work with fglrx though. I hope this helps.

---

