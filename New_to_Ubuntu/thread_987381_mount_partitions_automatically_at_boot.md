---
title: "mount partitions automatically at boot"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-11-19
hi,i installed intrepid,and just like always i went to the site of a script called diskmounter(which when run,causes the disk entries to be made in the fstab file,so that the partitions get automatically mounted at startup).but,i did not get it there?is there a way to make sure that all my partitions(two reiserfs,one fat32 and one ntfs) get mounted at startup?

---

### Post by MasterSander on 2008-11-19
yeah, edit /etc/fstab manually, could you do

```
 cat /etc/fstab 
``` and post output here.

Also make 4 maps to mount them in, then find the names of your partitions with fdisk -l  and post them here.

---

### Post by stonecoldjha on 2008-11-19
the output was:

sonu@sonu-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=1092eddd-f275-4958-8157-d2613b53918f /               reiserfs notail,relatime 0       1
# /dev/sda8
UUID=209ac442-22f6-4476-b332-dfa999ab02b7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
sonu@sonu-desktop:~$

---

### Post by stonecoldjha on 2008-11-19
the output of fdisk -l was:

sonu@sonu-desktop:~$ sudo fdisk -l
[sudo] password for sonu: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb91eb91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda3            3825       18172   115250310    5  Extended
/dev/sda4           18173       19457    10321762+   b  W95 FAT32
/dev/sda5            6330       11800    43945776   83  Linux
/dev/sda6           11801       18172    51183058+  83  Linux
/dev/sda7            3825        6280    19727757   83  Linux
/dev/sda8            6281        6329      393561   82  Linux swap / Solaris

Partition table entries are not in disk order
sonu@sonu-desktop:~$

---

### Post by stonecoldjha on 2008-11-20
what is to be done now?modifying the contents of fstab,but how?

---

### Post by taurus on 2008-11-20
Which partitions you want to mount and where do you want to mount them, mount points?

---

### Post by pluckypigeon on 2008-11-20
[http://ubuntuforums.org/showthread.php?p=6177625#post6177625](http://ubuntuforums.org/showthread.php?p=6177625#post6177625)

This will most definitely sort you out!!!!

---

### Post by stonecoldjha on 2008-11-20
i got psydm installed,and finally my drives mount at startup.thanks for that.but,now i can't shut down my system cleanly,whenever i try doing so,the system starts shutting down,but does not,ultimately i have to turn off the power switch.how do i solve this?

---

### Post by abybaddi on 2009-03-13
> **stonecoldjha said:**
> hi,i installed intrepid,and just like always i went to the site of a script called diskmounter(which when run,causes the disk entries to be made in the fstab file,so that the partitions get automatically mounted at startup).but,i did not get it there?is there a way to make sure that all my partitions(two reiserfs,one fat32 and one ntfs) get mounted at startup?

Just install "disk manager' it'll do all the work for you. It's GUI so easy to manage.

---

