---
title: "Booting OS X Leo from GRUB?"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Cam_B on 2008-10-22
Hi, I just installed OS X on a partition on my computer, I restarted and GRUB didn't pick up the new OS, so I did a little editing of the boot file and added in OS X, now I get error 13...

I am wondering how I can get GRUB to boot OS X without using a second hard drive because I don't have one lying around.

A screenshot of gparted is in the attachment. /dev/sda7 is where OS X is installed.

I probably don't have the menu.lst right, it is 

```

title		Mac OSX Leopard
rootnoverify	(hd0,6)
chainloader	(hd0,6)+1

```

Any help would be greatly appreciated.

---

### Post by Cam_B on 2008-10-22
I would really like some help on this issue, I am open to using other boot managers than GRUB, or even reinstalling everything.

---

### Post by phidia on 2008-10-23
This is a disallowed topic. 

You can find forums elsewhere on hackintosh.

---

