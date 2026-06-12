---
title: "Kubuntu can't read other paritions for install"
date: 2011-09-21
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by vtrader on 2011-09-21
Hi, I'm trying to install beta1, but in the manual disk setup it is unable to read the partition I want to install into.

My set up is this
sda
sda1 ntfs
sda2 ntfs

sdb
only sees as unused
but should be something like
sdb1 ntfs
sdb2 xfs
sdb3 swap
etc

I am trying to replace another distro, which is sharing with windows on sdb. sda is my primary windows install, sdb is split between windows and linux.

But it only sees sdb as unused, no partitions.

What to do?

thanks

---

### Post by ranch hand on 2011-09-21
Have you tried the Alt install disk?  That may give you better performance.

B2 is due out soon, you may want to wait.

If you are using the Live CD does gparted in the live session read all you drives and partitions correctly?  I would bet it does.  If so you could reformat the partition(s) you want to use with gparted and see if the installer will take your directions to use those partitions.  You would have to use the manual, or as I think may be the case with the current Ubuntu installer "something else" (very clear and concise) option.

Did you also check the md5sum on your download?

Did you use the option to check the disk for errors?

---

### Post by Quackers on 2011-09-21
What is the output of ```
sudo fdisk -lu
```

---

