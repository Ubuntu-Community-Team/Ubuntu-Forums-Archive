---
title: "mounting internal drives in terminal"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by sleeper414 on 2008-09-27
hi, i loved ubuntu so much, i decided to checkout ...xubuntu..debian, linux mint xfce and others.

the problem is the GUI sees my other hardrives, but the OS wont mount them

here is my information that i have so far.(this is running debian)
-------
debian:/home/chris# sudo fdisk -l

Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2373    19061091   83  Linux
/dev/hda2            2374        2482      875542+   5  Extended
/dev/hda5            2374        2482      875511   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb2               1        4865    39078081    c  W95 FAT32 (LBA)

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1           13036       19457    51584715    b  W95 FAT32
/dev/hdd3               1       13035   104703606    b  W95 FAT32

Partition table entries are not in disk order

and
----------------
sudo gedit /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


please help, im at my wits end!!!

---

### Post by perlluver on 2008-09-27
> **sleeper414 said:**
> hi, i loved ubuntu so much, i decided to checkout ...xubuntu..debian, linux mint xfce and others.

the problem is the GUI sees my other hardrives, but the OS wont mount them

here is my information that i have so far.(this is running debian)
-------
debian:/home/chris# sudo fdisk -l

Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2373    19061091   83  Linux
/dev/hda2            2374        2482      875542+   5  Extended
/dev/hda5            2374        2482      875511   82  Linux swap / Solaris

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb2               1        4865    39078081    c  W95 FAT32 (LBA)

Disk /dev/hdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1           13036       19457    51584715    b  W95 FAT32
/dev/hdd3               1       13035   104703606    b  W95 FAT32

Partition table entries are not in disk order

and
----------------
sudo gedit /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


please help, im at my wits end!!!

To add them to fstab, they will look like so ```
/dev/hdb2 /media/disk vfat defaults 0 0
``` vfat is for fat partitions, ntfs if for ntfs, all others Linux are ext3, or whatever they may be.  To mount them in the terminal you would type sudo mount -t vfat /dev/hdb1 /media/disk or where ever.  You might want to create folders for each, so ```
sudo mkdir -p /media/disk
``` and then own it ```
sudo chown username /media/disk
```

If you need more help post back.

---

