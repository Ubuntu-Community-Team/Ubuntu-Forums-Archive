---
title: "[SOLVED] Quick problem with a secondary (slave) drive"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by blackstar967 on 2008-07-17
Hey guys - just installed ubuntu today - decently happy with it.
I have a Dell desktop that has a 30 GB master drive with a 120 GB slave drive. Last night I was running XP, and I used dban's Boot and Nuke to get rid of everything on the 2 drives (stupid thing took about 10 minutes to boot, I was done with it!)

Now, after completely installing ubuntu 8.04, it doesn't recognize the 120 GB slave drive. The drive has no partitions or data on it (since it's completely clean). How do I get it to recognize it?
---------------------------------------------------------

when I run fdisk -l, I get the following:

Disk /dev/sdb:  120.0 GB
255 heads, 63 sectors, 14593 cylinders
Disk identifier: 0x0000000000 ----> this can't be right...

Disk /dev/sdb doesn't contain a valid partition table

---------------------------------------------------------

Thanks in advance!

---

### Post by phantomjoker on 2008-07-17
Very good peice of software - BARTpe - partition managment 

download it as a ISO image and burn it - then re boot.

its live so doesnt need any special installs.

Its really good - fast and it checks, scans and fixes so it practically does everything. 

Heres the link.   [http://www.nu2.nu/download.php?sFile=pebuilder3110a.exe]("http://www.nu2.nu/download.php?sFile=pebuilder3110a.exe")

Hope i helped..

---

### Post by blackstar967 on 2008-07-17
I'm not entirely sure what that is supposed to do, seeing as how I have no Windows installation files left :D

I just want ubuntu to recognize my second hard drive, so that I can use it to store random stuff.

---

### Post by philinux on 2008-07-17
Install and run gparted, the disk might need partitioning/formatting

---

### Post by blackstar967 on 2008-07-17
Oh wow. Thanks a bunch! Quite helpful.
So now, following the creation of a partition the size of the disk, I still get that it's "inactive". What now?

---

