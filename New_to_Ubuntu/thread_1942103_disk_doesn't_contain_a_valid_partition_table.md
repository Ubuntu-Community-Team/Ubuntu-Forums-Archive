---
title: "disk doesn't contain a valid partition table"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by kdureidy on 2012-03-16
Hi All

I am new here, I need your help

I installed ubuntu 11.10 on my Sony Vaio Z-Series laptop, but i cant see the NTFS partition.

I ran the **fdisk -l ** command, and here is the results:


VPCZ13SGX:~$ sudo fdisk -l
Warning: invalid flag 0x5520 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1511c129

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      963899      480926   83  Linux
/dev/sda4          980026   250079231   124549603    f  W95 Ext'd (LBA)
/dev/sda5   ?  3044036401   911322903  1081126899+   0  Empty

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/mapper/isw_cbfghhefc_Volume0: 128.0 GB, 128041877504 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250081792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x1511c129

                             Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cbfghhefc_Volume0p1            2048      963899      480926   83  Linux
/dev/mapper/isw_cbfghhefc_Volume0p4          980026   250079231   124549603    f  W95 Ext'd (LBA)
Partition 4 does not start on physical sector boundary.
/dev/mapper/isw_cbfghhefc_Volume0p5       129294336   250079231    60392448    7  HPFS/NTFS/exFAT
/dev/mapper/isw_cbfghhefc_Volume0p6          980028     5172929     2096451   82  Linux swap / Solaris
Partition 6 does not start on physical sector boundary.
/dev/mapper/isw_cbfghhefc_Volume0p7         5172993   129291119    62059063+  83  Linux
Partition 7 does not start on physical sector boundary.

Partition table entries are not in disk order

Disk /dev/mapper/isw_cbfghhefc_Volume0p1: 492 MB, 492468224 bytes
255 heads, 63 sectors/track, 59 cylinders, total 961852 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_cbfghhefc_Volume0p1 doesn't contain a valid partition table

Disk /dev/mapper/isw_cbfghhefc_Volume0p6: 2146 MB, 2146765824 bytes
255 heads, 63 sectors/track, 260 cylinders, total 4192902 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Alignment offset: 100352 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_cbfghhefc_Volume0p6 doesn't contain a valid partition table

Disk /dev/mapper/isw_cbfghhefc_Volume0p7: 63.5 GB, 63548481024 bytes
255 heads, 63 sectors/track, 7725 cylinders, total 124118127 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Alignment offset: 130560 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/isw_cbfghhefc_Volume0p7 doesn't contain a valid partition table

Disk /dev/mapper/isw_cbfghhefc_Volume0p5: 61.8 GB, 61841866752 bytes
255 heads, 63 sectors/track, 7518 cylinders, total 120784896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x6e697373

This doesn't look like a partition table
Probably you selected the wrong device.

                               Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cbfghhefc_Volume0p5p1   ?  1936269394  3772285809   918008208   4f  QNX4.x 3rd part
Partition 1 does not start on physical sector boundary.
/dev/mapper/isw_cbfghhefc_Volume0p5p2   ?  1917848077  2462285169   272218546+  73  Unknown
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_cbfghhefc_Volume0p5p3   ?  1818575915  2362751050   272087568   2b  Unknown
Partition 3 does not start on physical sector boundary.
/dev/mapper/isw_cbfghhefc_Volume0p5p4   ?  2844524554  2844579527       27487   61  SpeedStor
Partition 4 does not start on physical sector boundary.

Partition table entries are not in disk order
Warning: ignoring extra data in partition table 6
Warning: ignoring extra data in partition table 6
Warning: ignoring extra data in partition table 6
Warning: invalid flag 0x7365 of partition table 6 will be corrected by w(rite)

Disk /dev/mapper/isw_cbfghhefc_Volume0p4: 127.5 GB, 127538793472 bytes
255 heads, 63 sectors/track, 15505 cylinders, total 249099206 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Alignment offset: 101376 bytes
Disk identifier: 0xff3b1932

                               Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_cbfghhefc_Volume0p4p1       128314310   249099205    60392448    7  HPFS/NTFS/exFAT
/dev/mapper/isw_cbfghhefc_Volume0p4p2               1     4192903     2096451+   5  Extended
Partition 2 does not start on physical sector boundary.
/dev/mapper/isw_cbfghhefc_Volume0p4p5               2     4192903     2096451   82  Linux swap / Solaris
Partition 5 does not start on physical sector boundary.
/dev/mapper/isw_cbfghhefc_Volume0p4p6   ?   799238907  2400309345   800535219+  2f  Unknown
Partition 6 does not start on physical sector boundary.

Partition table entries are not in disk order

---

### Post by Hank_The_Dog on 2012-03-16
Is this a dual boot? I don't understand the question.

---

### Post by kdureidy on 2012-03-16
> **Hank_The_Dog said:**
> Is this a dual boot? I don't understand the question.

No its not a dual boot, I format laptop, removed windows 7, kept all the data in an NTFS partition, and installed ubuntu on the other partition.
now I can't access the NTFS partition.

when I open gparted, I see that NTFS partition exists, and I right lick on it and select information, I see this warning:
"failed to mount /dev/mapper/esw_sbfghhefc_volume0P5 doesnt have a valid NTFS"

---

### Post by oldfred on 2012-03-17
Were you running RAID? The dev mapper indicates RAID or LVM type partitions not standard MBR partitions.

Did you break the RAID when you installed Ubuntu? I really do not know RAID nor how to fix it.

---

### Post by kdureidy on 2012-04-12
> **oldfred said:**
> Were you running RAID? The dev mapper indicates RAID or LVM type partitions not standard MBR partitions.

Did you break the RAID when you installed Ubuntu? I really do not know RAID nor how to fix it.

Yes I did break RAID :(
i deleted RAID, re-partitioned the HDD, and now it works very well :D

---

