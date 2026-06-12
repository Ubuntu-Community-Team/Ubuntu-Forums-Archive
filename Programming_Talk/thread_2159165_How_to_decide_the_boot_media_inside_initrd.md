---
title: "How to decide the boot media inside initrd?"
date: 2013-07-02
forum: Programming Talk
---

### Post by macarthor on 2013-07-02
Hi all,

I'm customizing ubuntu 12.04.2 ISO. If I burn the ISO to CD and boot from CDROM, I get /dev/sr0 as the boot media, while I get /dev/sdb4 if I burn the ISO to USB stick.

So, I'd like to know how to decide the current boot media inside the RAMDISK, i.e., initrd.lz? My customized program needs to know it.

---

### Post by DJ_Max on 2013-07-02
Depends on what your program does. Devices are named depending on operating system and configuration. Boot devices aren't necessarily anything special. You can assume names, but you can be wrong. Explain what your program does and what it looks for in order for anyone to be of much help.

---

### Post by macarthor on 2013-07-03
> **DJ_Max said:**
> Depends on what your program does. Devices are named depending on operating system and configuration. Boot devices aren't necessarily anything special. You can assume names, but you can be wrong. Explain what your program does and what it looks for in order for anyone to be of much help.

hi,

My customized ubuntu ISO contains some customized files, and my program runs in RAMDISK (initrd.lz) and it would copy those customized files to HDD. So the program wanna know the device name of boot media, /dev/sdb4 for flash stick or /dev/sr0 for CDROM.

---

