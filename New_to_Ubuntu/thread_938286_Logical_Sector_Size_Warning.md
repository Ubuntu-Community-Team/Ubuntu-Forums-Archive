---
title: "Logical Sector Size Warning"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by March Felloworthy on 2008-10-04
Hi, everyone,

I've already got Ubuntu set up on an older PC, but I want to set up a dual boot on my main Windows box as well. When I run the installation process, though, I get as far as Step 3. When the installer tries to start up the partitioner, I receive this error message:

```

Warning!

Device /dev/sdb has a logical sector size of 2048.
Not all parts of GNU Parted support this at the moment,
and the working code is HIGHLY EXPERIMENTAL.

```

The "Starting up the partitioner..." progress bar then freezes at 46% (*Scanning disks...*).

What does this mean? Is there any way I can change the sector size?

ADDED IN EDIT: Aha! I finally did what I should have in the first place: Searched the forums. I found the post on how USB drives interfere with the installer, removed my iPod and flash drive and hey, presto! It works.

---

### Post by www.rzr.online.fr on 2008-11-11
hi

I have an issue w/ the same message :
  "Warning: Device /dev/sdb has a logical sector size of 2048"

on my mp3 device see :

[http://rzr.online.fr/q/fm](http://rzr.online.fr/q/fm)

---

### Post by jmcgovern on 2008-11-11
Same thing happened to me the first time I installed, and it bears repeating.   


*Unplug your iPod's/mp3 players/USB drives before installing Ubuntu.*  Unless of course your going to be installing to the USB drive.

---

### Post by malmjako on 2009-11-17
So what do I do if I want to install onto an external USB drive? parted complains because my sector size is 1024.

I've been successful in installing the base system onto a partition (created using fdisk), using the text based installer, mounting the partition on /target, skipping the partitioning during installation and installing the system. But I seem to be unable to install neither grub nor lilo. This is really annoying!

---

