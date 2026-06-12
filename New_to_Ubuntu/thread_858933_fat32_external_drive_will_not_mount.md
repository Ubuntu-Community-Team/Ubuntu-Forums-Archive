---
title: "fat32 external drive will not mount"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by nsabatino on 2008-07-14
I have a external USB drive which _used_ to mount automagically when it was plugged in, but now will not mount (still mounts on another, non-ubuntu machine).

Here's my attempt to do it myself:

FAT32 disk at /dev/sdb1 ...
> nsabatino@nsabatino01:~$ sudo fdisk -l
[sudo] password for nsabatino: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x48c248c1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38536   309540388+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x35d4ea6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976762552+   b  W95 FAT32

Make directory...
> sudo mkdir /media/nsabatino

Mount attempt 1:
> nsabatino@nsabatino01:~$ sudo mount -t FAT32 /dev/sdb /media/nsabatino
mount: unknown filesystem type 'FAT32'
mount: maybe you meant 'vfat'?

Whoops. Mount attempt 2:
> nsabatino@nsabatino01:~$ sudo mount -t vfat /dev/sdb /media/nsabatino
[sudo] password for nsabatino: 
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


WTF?

Tried what it suggested:
> [132959.909675] FAT: bogus number of reserved sectors
[132959.909697] VFS: Can't find a valid FAT filesystem on dev sdb.

---

### Post by ChameleonDave on 2008-07-14
Run a disk check.  Allow plenty of time.

```

sudo fsck.vfat -vatw /dev/sdb1

```

---

