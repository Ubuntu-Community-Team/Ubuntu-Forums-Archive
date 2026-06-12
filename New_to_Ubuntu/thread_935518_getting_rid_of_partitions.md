---
title: "getting rid of partitions?"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by Skyker on 2008-10-01
I have one Xubuntu partition and one XP pro partition.  Each about 9gigs.  I want to either make the XP parition as tiny as possible, or delete it all together...

and since I have everything working smoothly in Xubuntu, I think I might want to get rid of it all together.  How would I go about doing this?

---

### Post by bodhi.zazen on 2008-10-01
Just format the partition to ext3 or boot a live CD, fire up gparted, delete the partition, then grow your ubuntu partition into the free space (two steps).

---

### Post by Skyker on 2008-10-01
should i format it, will it merge with my other parition?  or should i go through the gparted way for that?

---

### Post by bodhi.zazen on 2008-10-01
Easiest thing would be to format it. You can do this from the command line.

```
mkfs.ext3 /dev/sdxx
```

Where sdxx === your NTFS partition. Just make sure you understand Linux Partition terminology.

You then edit fstab and add your partition.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=282018") 

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

The alternate would be to boot the Ubutnu CD and do it all with gparted.

[Gparted Documentation](http://gparted.sourceforge.net/documentation.php)

IMO neither option is "better", both will work.

---

