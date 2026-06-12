---
title: "mounting external drive"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by shredfitz on 2008-08-28
I have a newly installed 8.04 Ubuntu. I have an ipod and a 2.5" drive with my former installation of Ubuntu on it. The ipod connects without trouble.

The external drive is only visible if I go to 'places' and then to 'computer'. When I try to open the disk, I am given the message "Unable to Mount Location', 'can't mount file'

If I right click on the 'usb drive' icon that shows up under 'computer', I try to select 'mount volume' and nothing happens.

Thanks.

---

### Post by Titan8990 on 2008-08-28
Post the output of this command while the drive is connected to your computer:

sudo fdisk -l

---

### Post by shredfitz on 2008-08-28
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8f9a8f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5649    45375561    7  HPFS/NTFS
/dev/sdb2            5650        9729    32772600    f  W95 Ext'd (LBA)
/dev/sdb5            5650        9474    30724281   83  Linux
/dev/sdb6            9475        9729     2048256   82  Linux swap / Solaris

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
64 heads, 32 sectors/track, 28615 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

---

### Post by shredfitz on 2008-08-29
anyone?

---

### Post by kpkeerthi on 2008-08-29
> **shredfitz said:**
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4b36bdea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa8f9a8f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5649    45375561    7  HPFS/NTFS
/dev/sdb2            5650        9729    32772600    f  W95 Ext'd (LBA)
/dev/sdb5            5650        9474    30724281   83  Linux
/dev/sdb6            9475        9729     2048256   82  Linux swap / Solaris

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
64 heads, 32 sectors/track, 28615 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table

Which one of these are you trying to mount?

---

### Post by shredfitz on 2008-08-29
dev/sdc is the one I am trying to mount

---

### Post by kpkeerthi on 2008-08-29
> **shredfitz said:**
> 

Disk /dev/sdc: 30.0 GB, 30005821440 bytes
64 heads, 32 sectors/track, 28615 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x00000000

**[COLOR="Red"]Disk /dev/sdc doesn't contain a valid partition table[/COLOR]**

/dev/sdc is not formated. Boot with Ubuntu Live CD, go to System -> Admin -> Disks & Partition to [format]("http://gparted.sourceforge.net/livecd.php") it.

---

