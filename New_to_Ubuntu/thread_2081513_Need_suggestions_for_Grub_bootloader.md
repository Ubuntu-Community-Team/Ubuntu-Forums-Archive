---
title: "Need suggestions for Grub bootloader"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by anitest on 2012-11-07
Friends,

  I want the grub loader in CD drive(only grub file in CD) which points out my USB drive which is having bootable files to start booting. Can anyone give suggestions to edit the grub loader to make it to point out my USB device without changing anything in boot.ini or menu.lst of the system? Actually menu.lst or boot.ini will not include in this process. The grub in CD drive need to take care of loading OS from USB..

---

### Post by UltimateCat on 2012-11-07
Hi:

I looked around and found this:

How to Edit the Grub Boot Loader in Ubuntu 10.04
[http://ubuntuforums.org/showthread.php?t=1600542](http://ubuntuforums.org/showthread.php?t=1600542)

Not sure if your running Ubuntu 10.04 but these instructions should work for your distro-

And here is the full bootloader tutorial if you need it in the future:
[http://www.dedoimedo.com/computers/grub.html](http://www.dedoimedo.com/computers/grub.html)

---

### Post by anitest on 2012-11-07
Thanks Ultimatecat. 
Will check those links..

---

### Post by Cheesemill on 2012-11-07
Instead of trying to install Grub on a CD I would just use the Plop boot loader CD.

Booting from this will give you a menu that allows you to select your USB as the boot device.

[http://www.plop.at/en/bootmanagers.html](http://www.plop.at/en/bootmanagers.html)

Just burn the iso file included in the download.

---

