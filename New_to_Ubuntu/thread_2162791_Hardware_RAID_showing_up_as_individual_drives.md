---
title: "Hardware RAID showing up as individual drives?"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by TheDigitalOne on 2013-07-15
I picked up an inexpensive HP Microserver (658553-001) that has a 4-drive RAID system built in, added a 5th drive to host the OS and installed Ubuntu 13.04 with no problems. After all that I setup the hardware RAID via the HP tool at the BIOS prompt (RAID 1+0) (4) 3Tb drives mirrored and stripped.

Now when I boot up into Ubuntu it shows each individual drive, not the one RAID array.

Here is the fdisk report:
> Server:~$ sudo fdisk -l

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sde: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036731

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048   484483071   242240512   83  Linux
/dev/sde2       484485118   488396799     1955841    5  Extended
/dev/sde5       484485120   488396799     1955840   82  Linux swap / Solaris

Disk /dev/sdd: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdd doesn't contain a valid partition table



I expected to see one drive available, with 6Tb usable... Where did I go wrong?

Thanks!

---

### Post by newbie-user on 2013-07-16
Does the microserver use true hardware RAID or is it fakeRAID? You may have to set up a software RAID. FakeRAID is hit or miss.

---

