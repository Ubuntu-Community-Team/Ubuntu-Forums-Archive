---
title: "i ve installed linux in a 250gb disk, unable to partition-Gparted pops up error msg"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by prasaanth on 2008-09-22
i have installed my ubuntu in the a slave harddisk --250gb, (master is 80gb --windows xp running on it) but the thing is it is as a SINGLE PARTITION, when tried to resize/move thro Gparted in live cd i got errors, so i installed it on the complete disk without partitioning and after installation i tried again but this time some other error occured and the process terminated, please help.

Thanks in advance,

PRaNdo

---

### Post by bumanie on 2008-09-22
Post the output of > sudo fdisk -land post a screenshot of what gparted shows if possible.

---

### Post by prasaanth on 2008-09-23
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x62fc62fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2503    20105316    c  W95 FAT32 (LBA)
/dev/sda2            2504       10011    60308010    f  W95 Ext'd (LBA)
/dev/sda5            2504        5006    20105316    b  W95 FAT32
/dev/sda6            5007        7509    20105316    b  W95 FAT32
/dev/sda7            7510       10011    20097283+   b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe1d284c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30216   242709988+  83  Linux
/dev/sdb2           30217       30401     1486012+   5  Extended
/dev/sdb5           30217       30401     1485981   82  Linux swap / Solaris

is what my fdisk -l shows, btw i need to mount all the windows drives on ubuntu every time i load linux... manually.. any solution for that?

---

