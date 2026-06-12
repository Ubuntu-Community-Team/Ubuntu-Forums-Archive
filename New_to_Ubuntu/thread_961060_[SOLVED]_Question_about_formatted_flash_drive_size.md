---
title: "[SOLVED] Question about formatted flash drive sizes"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by ptn107 on 2008-10-27
So I just got a new 16gb flash drive and formatted it ext3 (all 16gb of it).  After formatting the final size is reported by Ubuntu as 16.2gb.  Places -> Computer, however, reports 165.8mb is in use already with 14.7gb remaining.  What is using the 165.8mb?  All I see on it is a 'lost+found' folder which is completely empty.  There is no trash on the drive either since I have not moved any files to [or from] it.  And before someone asks: I have also set the reserved blocks for root on the device to 0% when I formatted it.

Oh and in addition...
When I right-click on the drive in Places -> Computer the basic tab reports the volume size as 16.2gb, but on the volume tab the volume size is reported as 15.1gb.

What's going on?  Where is the free space going?

fdisk output:
```
Device Boot      Start         End      Blocks     Id  System
/dev/sdc1            1         1966     15791863+  83  Linux
```

df -h output:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1              15G  166M   15G   2% /media/disk-1
```

---

### Post by ptn107 on 2008-10-28
bump

---

### Post by ptn107 on 2008-10-28
bump

---

### Post by Paqman on 2008-10-28
All filesystems have a certain amount of overhead. So formatting a device will take up some space.

As for the device being reported as 15 or 16GB, I imagine that's due to the small discrepancy between a gigabyte (1024^3 bytes) and a gibibyte (1000^3 bytes). The two terms are used pretty interchangeably, which creates confusion, as one device seems to have two sizes.

---

