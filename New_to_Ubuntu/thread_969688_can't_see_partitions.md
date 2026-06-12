---
title: "can't see partitions"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by gregorio on 2008-11-03
I just installed Ubuntu 8.04 on a 250gb drive.  I set up the drive into three partitions plus swap.  I plan to use one partition for Ubuntu and the second maybe for a different distro.  The third I hope to use for data storage.  But when I open nautilus, the other two partitions are not there.  What do I do?

---

### Post by jbrown96 on 2008-11-03
You can't "see" partitions the way you are trying. When you installed Ubuntu, you said you created 4 partitions, did you give all of them filesystems( ext3, reiserfs, xfs, etc)? If you did not, you will not be able to use them. You can view your partition map with ```
sudo fdisk -l
``` in a terminal (app-->accessories-->terminal). If you did create file systems, you should be able to see them on your "places" menu or on the left side of nautilus. They are referenced by size. If not, you need to install gparted to create file systems, so you can use them. ```
sudo apt-get install gparted
``` and you can find gparted in system-->admin-->partition editor. Create partitions and then you can find them in nautilus or "places". If you are still having trouble post the output of ```
sudo fdisk -l
``` and take a screen shot of (print screen) gparted.

---

### Post by Duck2006 on 2008-11-03
From the terminal

sudo fdisk -l

and post the output.

---

### Post by gregorio on 2008-11-03
I copied and pasted the results of fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00045dd2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          24      192748+  83  Linux
/dev/sda2              25       10069    80686462+  83  Linux
/dev/sda3           10070       20111    80662365   83  Linux
/dev/sda4           20112       30401    82654425    5  Extended
/dev/sda5           20112       30158    80702496   83  Linux
/dev/sda6           30159       30401     1951866   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x908f908f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9728    78140128+  44  Unknown

Disk /dev/sdc: 257 MB, 257949696 bytes
16 heads, 32 sectors/track, 984 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         984      251888    e  W95 FAT16 (LBA)

hope this helps.  I'm not concerned with the windows drive at the moment.  thanks

---

### Post by gregorio on 2008-11-03
I guess I did make four partitions.

---

### Post by Duck2006 on 2008-11-03
Mount the partitions and you will see them.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

