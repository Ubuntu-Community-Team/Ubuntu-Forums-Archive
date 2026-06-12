---
title: "Can't detect pen drive after formatting in windows with fat32"
date: 2014-11-12
forum: New to Ubuntu
---

### Post by keshavparankusham on 2014-11-12
Recently I've bought a new pen-drive HP x705w 16gb which I gave it to an acquaintance, now it is not getting detected only in Ubuntu, so I formatted it using fat32 in windows, but still the problem persists, with only this pen-drive(I tried other pen-drives and they are working). The output I got for command ```
sudo fdisk -l
``` command is :

```

Disk /dev/sda: 500.1 GB, 500107862016 bytes255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0631f63b


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      411647      204800    7  HPFS/NTFS/exFAT
/dev/sda2          411648   462968831   231278592    7  HPFS/NTFS/exFAT
/dev/sda3       462970878   935811071   236420097    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/sda4       935811072   976773167    20481048    2  XENIX root
/dev/sda5       893868032   935811071    20971520   82  Linux swap / Solaris
/dev/sda6       462970880   893868031   215448576   83  Linux


Partition table entries are not in disk order


Disk /dev/sdc: 15.9 GB, 15892217856 bytes
255 heads, 63 sectors/track, 1932 cylinders, total 31039488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0036044e


This doesn't look like a partition table
Probably you selected the wrong device.


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?        2048    31039487    15518720    c  W95 FAT32 (LBA)



```
For some reason I'm not able to access the drive in Ubuntu, and the output of the command ```
mount /dev/sdb /mnt
``` is:
```
mount: no medium found on /dev/sdb
```

I also tried doing what is told in this link but of nothing improved. [http://askubuntu.com/questions/484976/usb-drive-not-recognized-ubuntu-14-04](http://askubuntu.com/questions/484976/usb-drive-not-recognized-ubuntu-14-04)

---

### Post by yancek on 2014-11-12
Your fdisk output does show it is being detected.  You could try the following command which includes the partition number shown and the filesystem type.  Post back results:

> sudo mount -t vfat /dev/sdc1 /mnt

---

### Post by keshavparankusham on 2014-11-12
Thanks for replying, I got the output as```
mount: special device /dev/sdc1 does not exist
```

---

### Post by keshavparankusham on 2014-11-12
Thank you for replying, I found this link [http://forums.opensuse.org/showthread.php/499538-Kernel-bug-unknown-partition-table-on-some-usb-flash-drives/page3](http://forums.opensuse.org/showthread.php/499538-Kernel-bug-unknown-partition-table-on-some-usb-flash-drives/page3) , I think he too had the same problem on the third page he told we can re format it from scratch using GParted, flash drive is working properly.

---

