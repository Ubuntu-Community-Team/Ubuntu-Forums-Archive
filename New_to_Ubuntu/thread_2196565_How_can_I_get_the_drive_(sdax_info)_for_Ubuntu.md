---
title: "How can I get the drive (sdax info) for Ubuntu?"
date: 2013-12-30
forum: New to Ubuntu
---

### Post by ruwan2 on 2013-12-30
Hi,
My computer has two Linux besides Windows XP. I would like to reinstall Ubuntu to another version 12.04. On start menu, it shows Ubuntu starts at dev/sda5. I remember it has another drive for user data (It may be home. I suspect that it is sda6). How can I get the drive (sdax info) for Ubuntu?


Thanks,



..............................................
jeff@M5100:~$ sudo fdisk -l
[sudo] password for jeff: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00003819

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   200833023   100415488    7  HPFS/NTFS/exFAT
/dev/sda2       200835070   320409599    59787265    5  Extended
/dev/sda3   *   320409600   348530687    14060544   83  Linux
/dev/sda4       348530688   390721535    21095424   83  Linux
/dev/sda5       200835072   273534975    36349952   83  Linux
/dev/sda6       273537024   312596479    19529728   83  Linux
/dev/sda7       312598528   320409599     3905536   82  Linux swap / Solaris

---

### Post by philinux on 2013-12-30
Please do not hijack other members threads, just start your own.

Moved to own thread.

---

### Post by thatredbird on 2013-12-30
It looks like three and four are you current Linux.  So logic suggests five and six are the other Ubuntu. From the info, three is the one you booted from.

---

### Post by steeldriver on 2013-12-30
You can see what partitions are mounted at what points in the filesystem using the mount command e.g.

```
mount | grep ^/dev
```

---

