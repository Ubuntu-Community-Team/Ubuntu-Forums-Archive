---
title: "[SOLVED] long hardy boot - waiting for root file system"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by MyR on 2008-07-04
Hello,

I installed a fresh copy of 8.04.1 and found that it takes a good 30 seconds longer to boot than it should.  I had the same problem with 8.04 and went back to gutsy; now I'm trying again.  My system is a laptop so boot time is very important.

I used startupmanager to display text during boot.  "waiting for root file system" is taking abnormally long.  The system boots fine, just slowly.

dmesg and bootchart are attached.  please help me resolve this problem.

```
fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a068f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         982     7887883+   7  HPFS/NTFS
/dev/sda2            7173        7296      996030   82  Linux swap / Solaris
/dev/sda3             983        7172    49721175   83  Linux

Partition table entries are not in disk order
```


thank you!

---

### Post by MyR on 2008-07-04
the workaround described here
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227003](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/227003)
works so far.

peace

---

