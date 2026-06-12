---
title: "error 22 and /home"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by dinny on 2008-05-15
okay this is my 5th attempt to install ubuntu
i install from 8.04 disk i select manual install
selected a partition of 10GIGs Logical EXT3 and i select /home fpr the mounting point when i try to continue it says no root file system is defined when i choose "/" as my mounting point when i restart i get a error 22 to be honest i dont even know what a mounting point is. can i please have some help i have been doing this for 6 hours! Thanks!

---

### Post by spiderbatdad on 2008-05-15
> Basic partitioning scheme.

Ubuntu (Linux) "requires" 2 partitions: / and swap. Both / and swap may be either Primary or Logical partitions.

    / = root min size 5 GB (Yes, I know you can go smaller if needed), 15-20 Gb may be better if you have the HD space.

    swap size

       1. RAM < 1 Gb swap = RAM X2.
       2. RAM > 1 Gb swap = 2 Gb

    Some claim a swap size of > 1 Gb is excessive. The 2 Gb recommendation is "conservative".


[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

### Post by EXCiD3 on 2008-05-15
Okay, here is the basics: If you want to create a separate /home partition you need two separate partitions: 1 for / (where ubuntu installs) and 1 for /home (where your settings are saved) and of course another one for swap equal to or greater than the size of ram in your system. Mounting points are the locations your partitions are put when you run ubuntu. Every drive must be "mounted" in order for it to be used. A "mount point" is a folder where the drive will be mounted to.

---

### Post by dinny on 2008-05-15
yes i understand how to partition it. my problems is when i try to move to the next step it says "no root file system is defined"
and my settings are
EXT3 10 gig logical , /home(mounting point)
2 gig swap
and i try to continue and i get that error

---

### Post by dinny on 2008-05-15
so i make 3 partitions?
like 10 gig logical 
2 gig swap and where is the /home go
and how big should my /home be

---

### Post by EXCiD3 on 2008-05-15
you need 3 partitions

2gb swap
10gb logical can be /
and have no /home

or

2gb swap (swap format)
smaller logical as / (ext3 format)
and remaining space as /home (ext3 format)

---

