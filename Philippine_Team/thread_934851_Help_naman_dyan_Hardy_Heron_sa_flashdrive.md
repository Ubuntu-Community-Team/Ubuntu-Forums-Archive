---
title: "Help naman dyan: Hardy Heron sa flashdrive"
date: 2008-10-01
forum: Philippine Team
---

### Post by mimicri8 on 2008-10-01
guys,

I have a laptop with vista on it. So since nauuso naman ang mga pendrive stuffs, nilagyan ko ung Sandisk Cruizer ko na 8gig ng Ubuntu 8. 

Ang problema ko, hindi ko maboot ung laptop kung wala ung pendrive. I mean may Error Message something like Grub loading error 21 ata or 15.

Kinakabahan ako pano kung mamisplace ko ung flashdive? Kung dedelete ko naman ung contents ng flashdrive including ubuntu 8 eh lalong patay na.

Halos di ko na nga ino-off tong laptop e. Haha.

Pano ko po ba unistall ung Ubuntu 8 sa flashdrive ko?
Help please.

---

### Post by loell on 2008-10-01
:lolflag:

hahah, kakaiba po ang problema nyo :D

pakiboot lang po sa ubuntu tapos tingnan natin yung grub menu.lst

```
cat /boot/grub/menu.lst
```

---

### Post by jsgotangco on 2008-10-01
well this shouldn't be the behavior. What you want to do is take back your MBR. Just boot the laptop in DOS and do fdisk /mbr to rewrite the master boot record so that vista is your default os to boot even if the usb is unplugged.

---

### Post by mimicri8 on 2008-10-08
Thank you for your reply :popcorn:

Please check these...

> **loell said:**
> :lolflag:

hahah, kakaiba po ang problema nyo :D

pakiboot lang po sa ubuntu tapos tingnan natin yung grub menu.lst

```
cat /boot/grub/menu.lst
```

Ito po...

```
title Ubuntu 8.04.1, kernel 2.6.24.19-generic
root hd(1,0)
kernel /boot/vmlinuz-2.6.24.19-generic...ro quiet splash
quiet

title Ubuntu 8.04.1, kernel 2.6.24.19-generic (recovery mode)
root hd(1,0)
kernel /boot/vmlinuz-2.6.24.19-generic...ro single
initrd /boot/initrd.img...generic

title Ubuntu 8.04.1, kernel 2.6.24.19-generic 
root hd(1,0)
kernel /boot/vmlinuz-2.6.24.19-generic...ro quiet splash
initrd /boot/initrd.img...generic
quiet

title Ubuntu 8.04.1, kernel 2.6.24.19-generic (recovery mode)
root hd(1,0)
kernel /boot/vmlinuz-2.6.24.19-generic...ro single
initrd /boot/initrd.img...generic

title Ubuntu 8.04.1, memstest86+
root hd(1,0)
kernel /boot/memstest.bin
quiet

title other operating system
root

#This entry automatically added by Debian installer for non-linux OS
#on /dev/sda1

title Windows Vista/Longhorn (Loader)
root (hd0,0)
savedefault
makedefault
chainloader +1

#This entry automatically added by Debian installer for non-linux OS
#on /dev/sda2

title Windows Vista/Longhorn (Loader)
root (hd0,1)
savedefault
makedefault
chainloader +1


```


Err..does this have to do with the (hd x,y)? 
Or ung savedefault makedefault thingy @_@ 



> **jsgotangco said:**
> well this shouldn't be the behavior. What you want to do is take back your MBR. Just boot the laptop in DOS and do fdisk /mbr to rewrite the master boot record so that vista is your default os to boot even if the usb is unplugged.

Kelangan ko po ba dito ng bootdisk like ung windows 98 :confused:


What to do next? :lolflag:

---

### Post by loell on 2008-10-08
yep, just follow sir jerome's advice as you shouldn't need grub in booting ubuntu usb disk anyway.

---

### Post by ysNoi on 2008-10-08
Or you can go to Repair Option of your OS and type FIXMBR there..! :guitar:

---

