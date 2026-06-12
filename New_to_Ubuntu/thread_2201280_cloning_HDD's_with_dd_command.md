---
title: "cloning HDD's with dd command"
date: 2014-01-23
forum: New to Ubuntu
---

### Post by castle1500 on 2014-01-23
I recently cloned my encrypted Windows 7 HDD using Ubuntu 10.10 and the dd command - dd if=/dev/sda of=/dev/sdb.  The original HDD and the new HDD were the same size, and I wanted to make an exact copy(all partitions)  so it was no big deal.  Tested and booted just fine. 

But,  what if the new HDD is larger?  Can I use the same command and use GParted to extend the partitions on the rest of the empty new HDD even thought the original is encrypted?

---

### Post by whitesmith on 2014-01-23
Free space is not encrypted.

---

### Post by tgalati4 on 2014-01-23
You might get an error from gparted that says something like:  "Partition table size does not match physical disk size, do you want to correct?".  Hit yes then the last partition on the disk will be able to extend to the rest of the disk.  Not sure if encryption will interfere with this process.

---

