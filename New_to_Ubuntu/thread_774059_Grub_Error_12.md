---
title: "Grub Error 12"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by jcrnan on 2008-04-29
When I installed Ubuntu 8.04 it didn't see my XP disc and Im having no luck getting Grub to load the XP partition.

nan@the-holy-laptop:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdabedabe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         892     7164958+  83  Linux
/dev/sda2            9715       10006     2345490   82  Linux swap / Solaris
/dev/sda3             893        9714    70862715   83  Linux
/dev/sda4           10007       12160    17302005    f  W95 Ext'd (LBA)
/dev/sda5           10007       12160    17301973+   7  HPFS/NTFS

Partition table entries are not in disk order


That is what I have now and the grub menu.lst looks like this:

default 0
timeout 3

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=893bee1a-46aa-44e2-84f4-4d42258c5cd2 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=893bee1a-46aa-44e2-84f4-4d42258c5cd2 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

title Win XP
root (hd0,4)
chainloader +1
makeactive

When I choose the XP from Grub I get a Grub Error 12. What is the problem here?

---

### Post by hermes0710 on 2008-04-29
Try removing line chainloader +1 from Win XP session

Check this though:

12 : "Cannot mount selected partition"

This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

[http://www.uruk.org/orig-grub/errors.html]("http://www.uruk.org/orig-grub/errors.html")

---

### Post by jcrnan on 2008-05-05
That didnt work :/ Same error still. Im kinda confused as the windows partition seems to be and should be completely intact.

---

### Post by jcrnan on 2008-05-07
Nobody that can help me with this? I can acsess all my files just fine from Ubuntu but booting windows seems impossible. How do I use grub properly here to get this working?

---

### Post by mapes12 on 2008-05-07
This thread may be helpful:

[http://ubuntuforums.org/showthread.php?t=740221](http://ubuntuforums.org/showthread.php?t=740221)

---

