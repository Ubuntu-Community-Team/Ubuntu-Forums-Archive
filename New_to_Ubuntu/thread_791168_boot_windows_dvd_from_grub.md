---
title: "boot windows dvd from grub?"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by The Titan on 2008-05-11
I have a old laptop, gateway solo 9200.  It has a dvd drive and can read all my dvd's from ubuntu, which, installed perfectly. but wont boot from them.  I want to make my laptop dual boot but i only have a windows DVD, and i was wondering if it would be possible to boot the dvd, from grub?? I may be way off, but it's worth a shot i guess..

---

### Post by Jimmey on 2008-05-12
You need to check the boot order in the computer's BIOS - Usually at the boot screen it will say something similar to "Press F12 to enter setup" - Make sure that the computer's set to boot from a CD-ROM before it attempts to boot from a hard drive.

---

### Post by Joeb454 on 2008-05-12
You need to change your boot sequence in the BIOS, some PC's allow you to specify it without changing the BIOS.

GRUB loads after this option has passed :)

---

