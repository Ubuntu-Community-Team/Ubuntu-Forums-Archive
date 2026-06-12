---
title: "Is there any tool to reflash a flash drive for Ubuntu?"
date: 2013-03-10
forum: New to Ubuntu
---

### Post by Doj on 2013-03-10
I've just tried to fix a flash drive from my friend which was unable to write a partition table on (a computer at his school messed it up). dding null to it seemed to corrupt it, as the next time I tried dd something onto it it basically said the flash had 0 bytes available. I thought it may have messed up the controller's flash, so I did some research, eventually finding SSS_MP_Utility for Windows from flashboot.ru which would flash a .bin to the flash drive's controller chip (firmware). This utility did work, so I now have a new Kingston 16GB flash drive.

I was wondering if there was anything similar for Linux, or a way to directly access the hardware before it gets to /dev/sdb?

Sorry if this is in the wrong place.

Thanks, Jodie.

---

### Post by kabukiM0n0 on 2013-03-10
Gparted is maybe what you are looking for?

---

### Post by sudodus on 2013-03-10
> **Doj said:**
> I've just tried to fix a flash drive from my friend which was unable to write a partition table on (a computer at his school messed it up). dding null to it seemed to corrupt it, as the next time I tried dd something onto it it basically said the flash had 0 bytes available. I thought it may have messed up the controller's flash, so I did some research, eventually finding SSS_MP_Utility for Windows from flashboot.ru which would flash a .bin to the flash drive's controller chip (firmware). This utility did work, so I now have a new Kingston 16GB flash drive.

I was wondering if there was anything similar for Linux, or a way to directly access the hardware before it gets to /dev/sdb?

Sorry if this is in the wrong place.

Thanks, Jodie.

This is very interesting. Thanks for sharing :KS

I don't know, if there is something similar for linux. On the other hand, this might solve the problem, that several people describe in current threads at the Ubuntu Forums. After all, it's easy to find a Windows computer ;-)

---

### Post by ViliX64 on 2013-03-10
Maybe this could be helpful for you: [http://forum.xda-developers.com/showthread.php?t=1470910](http://forum.xda-developers.com/showthread.php?t=1470910).

---

