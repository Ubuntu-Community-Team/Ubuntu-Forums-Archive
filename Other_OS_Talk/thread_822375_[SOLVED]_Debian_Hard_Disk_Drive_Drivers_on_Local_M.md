---
title: "[SOLVED] Debian: Hard Disk Drive Drivers on Local Mirror Created Using CD"
date: 2008-06-08
forum: Other OS Talk
---

### Post by gmjs on 2008-06-08
Hi.  I've had this posted on the Debian forums for a while with no reply.  Maybe the Ubuntu forums can help me?

I've previously set up a TFTP and web server on a small network for installing Ubuntu. The web server contains a copy of the alternate installation CD. I've read several 'HowTos' stating that you should create the mirror using a piece of software (e.g. apt-mirror) but, until now, have found that copying the contents of the alternate install CD (save for verison 7.04) works just as well.

However, with the Debian Etch CD 1, it seems that the drivers I need for detecting a hard disk drive are missing. An install from my local 'mirror' doesn't work as no HDD is detected, but selecting an official mirror downloads the appropriate driver and detects the disk with no problems. The CD has a known-good image.

Does anyone know why this is happening and, if necessary, how to modify the 'mirror' to make it work?  I have had the same problem with three different (eIDE) HDDs, but with my limited knowledge of the debian-installer, I'm stuck. I'm using the Debian 4 r3 CD 1.

Any help would be greatly appreciated.

Thanks,

Graham

---

