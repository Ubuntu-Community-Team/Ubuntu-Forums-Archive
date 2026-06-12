---
title: "Mounting my /home in Sidux"
date: 2009-02-04
forum: Other OS Talk
---

### Post by ifflejink on 2009-02-04
So, I just installed Sidux, but I couldn't mount my /home at install, since my username for the install is the same as the username for my /home partition (/home/gavin, with my username being gavin). /dev/sda4 is my /home partition, and is using xfs.

Here's my fdisk -l output:
```
root@Srivijaya:/home/gavin# fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc718c718

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1401    11253501    5  Extended
/dev/sda4            1402       14593   105964740   83  Linux
/dev/sda5               1         127     1020064+  82  Linux swap / Solaris
/dev/sda6             128        1401    10233373+  83  Linux

```

Here are the contents of my fstab, which seem to indicate that my partition is mounted somehow. My /media shows a disk1part4 option, but that is completely empty, and gparted verifies that the partition does definitely have data on it.

<dump> <pass>

UUID=0cb0723c-2f50-49f5-9bd3-2c6c933b5383     /media/disk1part4              xfs             auto,users,rw,exec,noatime                 0      2

UUID=66b6cad4-8c6f-44c1-955f-0abd0b841236     none                           swap            sw                                         0      0

UUID=ba85631a-679e-4672-b8c0-6555ee212bc7     /                              ext3            defaults,errors=remount-ro,noatime         0      1

/dev/cdrom                                    /media/cdrom                   udf,iso9660     noauto,ro,users                            0      0


Thanks for the help!

---

