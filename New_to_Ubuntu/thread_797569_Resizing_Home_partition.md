---
title: "Resizing Home partition"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by saldie on 2008-05-17
Hi, I love Hardy so much that I would like to shrink my Vista partition and increase my Home partition, but I am having problems doing so.
My disk is set up as follows:
/dev/sda1- Vista 
/dev/sda2- Root 
/dev/sda3-swap
/dev/sda4-Home

I know how to shrink my Vista partition with gparted, but it does not matter is I put the free space in front of /sda1 or in between /sda1 and /sda2, I cannot increase the size of my Home partition.
Anyone know what I am doing wrong?
Thanks.

---

### Post by philinux on 2008-05-17
From what I've read the process is this.

Clean up
Defrag twice
resize vista with it's own partition manager.

---

### Post by saldie on 2008-05-17
I already tried that.
When I use Vista to shrink its partition it creates free space between /sda1 and /sda2, then when I use gparted to increase Home partition it wont let me. I can only resize /sda2.

---

### Post by Crossroads on 2008-05-17
That is because the free space is "between" sda1 and sda2
And partitions have to use contiguous space, so the only option for GPArtEd is to add the free space to sda1.

But I've read elswehere on this forum that changing the start position of a partition takes ages (hours or even days, I saw in one post).

Is there any chance of backing up your files and doing a reinstall manually? Then you can define all three partition sizes.

---

### Post by saldie on 2008-05-17
I've been goggling around and I think you are right.
Seems that you can only resize a partition if free space is next to it.
I wonder if this is true of all file systems or just ext3?
Thanks.

---

### Post by Crossroads on 2008-05-17
All, as far as I know

But could you create a new partition in that free space then assign a mount point to it, so that some of your filesystem can go in it?

or, have a look at Logical Volume Management

[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)

[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)

HTH

---

