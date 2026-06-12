---
title: "Can't Boot Ubuntu"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by GuitarRocker2562 on 2008-09-01
Hi, I just upgraded XP to Vista, totally forgeting that Vista's bootloader would overwrite my GRUB install. Now I can't boot into Ubuntu, anyone know how I can fix this?

---

### Post by Gone fishing on 2008-09-01
This is how to fix grub

Boot up on the live CD
Open a terminal and type:

sudo grub

> root (hd0,0)

> setup (hd0)

> exit

This is assuming your Ubuntu partition is at hd0,0 the first hard drive and the first partition on that drive, If not, then adjust accordingly. (To find where your Ubuntu boot partition is if you don't know, after sudo grub type "find /boot/grub/stage1" and use that value. (If you not sure how grub names disks have a look at: [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto))

This isn't quit how I do it I put grub on my Linux partition (hd0,0) (in this case) (> setup (hd0,0)) and then use the GAG boot loader gag.sourceforge.net

---

### Post by GuitarRocker2562 on 2008-09-01
Sorry, forgot to mention the hard part. I don't have a CD Drive or a flash drive larger than 256MB (so anything small for a bootable drive that would help would work.)

---

### Post by WRDN on 2008-09-01
You can use [Super Grub Disk]("http://www.supergrubdisk.org/") to restore the GRUB bootloader. This is less than 1Mb.

---

### Post by GuitarRocker2562 on 2008-09-01
Thanks, I will give it a try!

---

