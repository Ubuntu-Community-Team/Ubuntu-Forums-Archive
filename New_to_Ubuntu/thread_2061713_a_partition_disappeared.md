---
title: "a partition disappeared"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by dupa on 2012-09-23
On my HD I've four partitions

/
/home
/opt
swap

Three of them are working correctly.
On the last boot I noticed the system was hanging.. playing around with recovery mode I discovered it seems to not work anymore the /opt partition.

I commented its line in /etc/fstab and now the system boots correctly (but some software I had installed in /opt of course doesn't exist anymore).

Now (the system is up and running) I de-commented the /opt line in /etc/fstab and i got this


```
sudo mount /opt 
mount: special device UUID=72874e17-0a4d-4386-b4df-e9982c129c02 does not exist
```

Going in this utility, SMART status says the disk is healthy...

---

### Post by dupa on 2012-09-23
One more info
if I execute
```
sudo blkid
```

I see the ID of / and /home but there is no entry for /opt !

---

### Post by Wim Sturkenboom on 2012-09-23
So what is the output of _sudo fdisk -l_ (lower case L at the end); just checking if the partition still exists ;)

```

wim@i3-2120:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd2efff31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   511999999   255896576    7  HPFS/NTFS/exFAT
/dev/sda3       512000000   528001023     8000512   82  Linux swap / Solaris
/dev/sda4       528003070  1953523711   712760321    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       528003072   820969471   146483200   83  Linux
/dev/sda6       820971520  1953523711   566276096   83  Linux

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e192e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    52436159    26218048+   7  HPFS/NTFS/exFAT
/dev/sdb2        52436221   472655871   210109825+   f  W95 Ext'd (LBA)
/dev/sdb5        52436223   115346699    31455238+   7  HPFS/NTFS/exFAT
/dev/sdb6       115346763   167782859    26218048+   b  W95 FAT32
/dev/sdb7       167782923   220219019    26218048+  83  Linux
/dev/sdb8       220219392   228579327     4179968   82  Linux swap / Solaris
/dev/sdb9       228581376   472655871   122037248   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3c8c2717

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  1953520064   976760001   83  Linux
wim@i3-2120:~$ 

```

---

