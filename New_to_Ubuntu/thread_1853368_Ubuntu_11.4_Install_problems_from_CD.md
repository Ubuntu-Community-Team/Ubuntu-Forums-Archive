---
title: "Ubuntu 11.4 Install problems from CD"
date: 2011-10-02
forum: New to Ubuntu
---

### Post by blindscout on 2011-10-02
Okay first of all, I've installed Ubuntu 10 successfully on 2 computers in the past, so I'm pretty much convinced its hardware issues I'm having but I'll give it a try here.


-Created a bootable CD by burning the direct iso image I got from the ubuntu site.
-Boots okay, but when the first orange screen comes up with the "keyboard = human" like-equation, unless I press any key within the next few seconds, it goes to a black screen with a blinking cursor and responds to nothing.
-So I press Enter when the orange screen appears and the language settings come up along with the options.
-I choose English and press F6 to change "quiet splash" to "text" so I can see what's happening.
-I select Install Ubuntu.
-A bunch of text appears and it freezes at these points:

[ 9.445825] [drm] failed to find VBIOS tables
[ 9.453193] nouveau 0000:01:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 9.458738] vgaarb: device changed decodes: PCI:0000:00:02.0, olddecodes=io+mem,decodes=none:owns=none



I suspect my VGA is the issue here but I'll leave it to you guys.
My VGA is an nVidia GeForce MX440 (AGP 8x, 64MB) and other PC specs are:

Intel® Desktop Board D845GLLY
Intel Pentium 4 1.70Ghz
512 RAM
pretty much it?

Hope you guys can help me.
Thanks.

---

### Post by Quackers on 2011-10-02
Try the nomodeset boot option

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

