---
title: "Need help adding Sabayon to my GRUB List..."
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Crafty Kisses on 2008-06-03
I can't seem to get Sabayon to my GRUB List, I only have Ubuntu 8.04, does anyone have any ideas? 

I've done this:
```
title Sabayon
root /
chainloader +1
```

The HDD with Sabayon is called "/" so how would I do that in the GRUB.menu any ideas? Thanks!

---

### Post by Inxsible on 2008-06-03
Grub works differently. You need to know the hard drive number and the partition number of the install.

it should look something like```
root (hd0,0)
```What that means is 

hd0 -- 1st hard drive
0 -- 1st partiton

yes...grub has zero-based numbering.

EDIT: Post the output of ```
sudo fdisk -l
``` and point out which partition has your Sabayon install. I can then give you the exact line to put in grub.

---

### Post by Crafty Kisses on 2008-06-03
> **Inxsible said:**
> Grub works differently. You need to know the hard drive number and the partition number of the install.

it should look something like```
root (hd0,0)
```

How would I find out which one Sabayon is on? I know Ubuntu is on (hd0,0) but not sure about Sabayon.

---

### Post by Inxsible on 2008-06-03
> **Codename said:**
> How would I find out which one Sabayon is on? I know Ubuntu is on (hd0,0) but not sure about Sabayon.

See my EDIT: section in the above post. :)

---

### Post by Crafty Kisses on 2008-06-03
> **Inxsible said:**
> Grub works differently. You need to know the hard drive number and the partition number of the install.

it should look something like```
root (hd0,0)
```What that means is 

hd0 -- 1st hard drive
0 -- 1st partiton

yes...grub has zero-based numbering.

EDIT: Post the output of ```
sudo fdisk -l
``` and point out which partition has your Sabayon install. I can then give you the exact line to put in grub.

Here ya go:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f8869e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7165    57552831   83  Linux
/dev/sdb2            7166        7476     2498107+   5  Extended
/dev/sdb5            7166        7476     2498076   82  Linux swap / Sol
```

---

### Post by sisco311 on 2008-06-03
If you have a menu.lst on the sabayon partition, then just copy and paste the grub entry from there.

---

### Post by Crafty Kisses on 2008-06-03
> **sisco311 said:**
> If you have a menu.lst on the sabayon partition, then just copy and paste the grub entry from there.

I can't access it, it won't let me.

---

### Post by Inxsible on 2008-06-03
Codename, you didn't mention which of your drives has Sabayon sda or sdb?

But I will give you the grub lines for both...

if its on sda```
root (hd0,0)
```if its on sdb```
root (hd1,0)
```

EDIt: Oh i think you did mention in one of your posts that Ubuntu was on (hd0,0)....yeah so it will be sdb where your Sabayon is....Use the root (hd1,0) in the grub

---

### Post by Crafty Kisses on 2008-06-03
> **Inxsible said:**
> Codename, you didn't mention which of your drives has Sabayon sda or sdb?

But I will give you the grub lines for both...

if its on sda```
root (hd0,0)
```if its on sdb```
root (hd1,0)
```

EDIt: Oh i think you did mention in one of your posts that Ubuntu was on (hd0,0)....yeah so it will be sdb where your Sabayon is....Use the root (hd1,0) in the grub

Oh ok, thanks!

---

### Post by Crafty Kisses on 2008-06-03
> **Inxsible said:**
> Codename, you didn't mention which of your drives has Sabayon sda or sdb?

But I will give you the grub lines for both...

if its on sda```
root (hd0,0)
```if its on sdb```
root (hd1,0)
```

EDIt: Oh i think you did mention in one of your posts that Ubuntu was on (hd0,0)....yeah so it will be sdb where your Sabayon is....Use the root (hd1,0) in the grub

Ok, I switched it to (hd1,0) and when I tried booting up into Sabayon I got this error:
```
Invalid or unsupported executable format
```
Any ideas?

This is the input in my menu.lst
```
title Sabayon
root (hd1,0)
chainloader +1
```

---

### Post by Crafty Kisses on 2008-06-03
> **Codename said:**
> Ok, I switched it to (hd1,0) and when I tried booting up into Sabayon I got this error:
```
Invalid or unsupported executable format
```
Any ideas?

This is the input in my menu.lst
```
title Sabayon
root (hd1,0)
chainloader +1
```

Bump.

---

### Post by Crafty Kisses on 2008-06-05
I found the fix for this, you have to boot up into Sabayon first, then open up your grub.conf file, by doing the following:
```
su
```
Enter your password, then do the following:
```
sudo nano /boot/grub/grub.conf
```
Add the following lines into your grub.conf file:
```
title		Ubuntu 8.04, kernel 2.6.24-17-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=9564d0bc-5dec-45c4-b689-bbf1d25d3e7c ro quiet splash
initrd		/boot/initrd.img-2.6.24-17-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-17-generic root=UUID=9564d0bc-5dec-45c4-b689-bbf1d25d3e7c ro single
initrd		/boot/initrd.img-2.6.24-17-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
```

Then you want to save your changes:
```
Cntrl+W
```
Reboot, and Ubuntu should be on the Sabayon boot loader.

---

