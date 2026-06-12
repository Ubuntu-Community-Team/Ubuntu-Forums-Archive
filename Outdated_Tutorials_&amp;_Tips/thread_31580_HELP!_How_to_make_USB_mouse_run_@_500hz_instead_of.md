---
title: "HELP! How to make USB mouse run @ 500hz instead of 125hz ?"
date: 2005-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by maniac99 on 2005-05-03
Hi there :)

Ok, so Linux by default runs the USB mouse at 125hz.  Which is pretty damn slow.  Some people are even using ps2 mice so they can get a maximum of 200hz.

I found this site which provides a link to a .patch file which can be used to patch a kernel [http://www.linux-gamers.net/modules/wfsection/article.php?articleid=62](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=62) and also here (another one) [http://lkml.org/lkml/2005/2/7/142](http://lkml.org/lkml/2005/2/7/142)

The thing is, it doesn't work.  In make menuconfig I can see under USB-Inputs the new option which you change to 2, and it changes the mouses responsiveness from 10ms to 2ms.  However, on reboot of the new kernel, doing cat /proc/bus/usb/devices shows that the mouse is still running at the old 10ms - not 2ms :(

Anyone know how I can fix this?

---

### Post by poofyhairguy on 2005-05-04
[QUOTE=maniac99]
Anyone know how I can fix this?[/QUOTE]

Howdy. For something this....well...tweakish the only place on the whole internet where it will be found is on the gentoo forums-

[http://forums.gentoo.org/viewtopic-t-164679-highlight-500mhz+mouse.html](http://forums.gentoo.org/viewtopic-t-164679-highlight-500mhz+mouse.html)

---

