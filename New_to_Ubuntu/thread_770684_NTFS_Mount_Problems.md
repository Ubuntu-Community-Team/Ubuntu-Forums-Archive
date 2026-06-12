---
title: "NTFS Mount Problems"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by bamend on 2008-04-27
All of a sudden Ubuntu won't mount my NTFS drives.  What can I check.

---

### Post by tamoneya on 2008-04-27
post the output of ```
sudo fdisk -l
```From there we can tell you what to run to mount your ntfs drives

---

### Post by bamend on 2008-04-27
Disk /dev/sda: 30.7 GB, 30758289408 bytes
255 heads, 63 sectors/track, 3739 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbbc6bbc6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3738    30025453+   7  HPFS/NTFS

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09f2c1d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               2       24792   199133707+   f  W95 Ext'd (LBA)
/dev/sdb5               2       12749   102398278+   7  HPFS/NTFS
/dev/sdb6           12750       15299    20482843+   7  HPFS/NTFS
/dev/sdb7           15300       17864    20603331    7  HPFS/NTFS
/dev/sdb8           17865       20414    20482843+   7  HPFS/NTFS
/dev/sdb9           20415       24792    35166253+   7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc5c2f943

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         608     4883728+  82  Linux swap / Solaris
/dev/sdc2             609        2432    14651280   83  Linux
/dev/sdc3            2433       14593    97683232+  83  Linux

---

### Post by bodhi.zazen on 2008-04-27
mount the partition manually and post any error message. You mount it by the mount point.

```
sudo mount /media/xxx
```

where /media/xxx is where the partition is mounted.

Then you can also check dmesg

```
dmesg | tail
```

---

### Post by tamoneya on 2008-04-27
```
sudo mkdir /windows
sudo mount -t ntfs /dev/sdb5 /windows
```

---

