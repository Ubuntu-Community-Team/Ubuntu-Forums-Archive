---
title: "Unsure about Disk Partation"
date: 2012-11-28
forum: New to Ubuntu
---

### Post by DaveMcC on 2012-11-28
Have a new sata drive here from a netbook, which I am trying to reformat to install, win / lunbuntu.  I keep getting a warning message

The partition is misaligned by 512 bytes.  This may result in very poor performance.
Repartitioning is suggested

I have been "repartitioning" the drive but keep running into the same warning,  also I am unable to install XP

I wanted to have a dual boot system, 80gb with XP 260gb lubuntu

What am I doing wrong not to be able to repartition the hard drive

Dave

---

### Post by Pilot6 on 2012-11-28
Partition the drive using gparted. It has default option "Align to MiB". All problems with alignment will be solved. The partitioner used in Ubuntu installer does not work well with HDD's with 4kB sectors.

---

### Post by DaveMcC on 2012-11-28
> **Pilot6 said:**
> Partition the drive using gparted. It has default option "Align to MiB". All problems with alignment will be solved. The partitioner used in Ubuntu installer does not work well with HDD's with 4kB sectors.


Thanks for that.

Now if I could only get the cooling fan replaced in this NetBook, it would be back to new, or better now that win7 is removed 

Dave

---

