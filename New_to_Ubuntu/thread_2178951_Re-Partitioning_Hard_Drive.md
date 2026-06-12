---
title: "Re-Partitioning Hard Drive"
date: 2013-10-05
forum: New to Ubuntu
---

### Post by taylor5 on 2013-10-05
I am running a dual-boot machine with Windows 7 and Ubuntu, but I have a bit of a problem. When I originally partitioned my hard drive for Ubuntu, I was low on disk space, so Ubuntu only got about 25 GB worth of space. I freed up some space, and now Windows has over 100 GB, but Ubuntu still only has 25 GB. So is there a way to partition it again to give Ubuntu, say 75 GB?

---

### Post by heir4c on 2013-10-05
Maybe you can keep that like it is. Use the free space you want to give to Ubuntu for storage of data, foto, documents, ...
From Ubuntu you can always get to that partition to use the files.
How many partitions have you?
Open a terminal and type:
```
fdisk -l
```
Post the output here.
ThanX

---

### Post by taylor5 on 2013-10-05
> **heir4c said:**
> Maybe you can keep that like it is. Use the free space you want to give to Ubuntu for storage of data, foto, documents, ...
From Ubuntu you can always get to that partition to use the files.
How many partitions have you?
Open a terminal and type:
```
fdisk -l
```
Post the output here.
ThanX

I typed it and nothing happened.

---

### Post by SuperFreak on 2013-10-05
Try
```
sudo fdisk -l
```

[http://www.tecmint.com/fdisk-commands-to-manage-linux-disk-partitions/]("http://www.tecmint.com/fdisk-commands-to-manage-linux-disk-partitions/")

---

### Post by taylor5 on 2013-10-06
> **heir4c said:**
> Maybe you can keep that like it is. Use the free space you want to give to Ubuntu for storage of data, foto, documents, ...
From Ubuntu you can always get to that partition to use the files.
How many partitions have you?
Open a terminal and type:
```
fdisk -l
```
Post the output here.
ThanX

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x375b9de6


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    25767935    12843008    7  HPFS/NTFS/exFAT
/dev/sda3        25767936   923069439   448650752    7  HPFS/NTFS/exFAT
/dev/sda4       923070462   976771071    26850305    5  Extended
/dev/sda5       923070464   968388607    22659072   83  Linux
/dev/sda6       968390656   976771071     4190208   82  Linux swap / Solaris

---

### Post by heir4c on 2013-10-06
I think it show not all of the space you have on the HD, so:
Use cfdisk to see more:

```
cfdisk
```

(or with sudo if it don't work without)
Select all text with your mouse and copy that and post it here.

(Press Q to exit cfdisk)

---

### Post by kmb9205 on 2013-10-06
i've found sudo fdisk -l to work

---

### Post by taylor5 on 2013-10-06
> **heir4c said:**
> I think it show not all of the space you have on the HD, so:
Use cfdisk to see more:

```
cfdisk
```

(or with sudo if it don't work without)
Select all text with your mouse and copy that and post it here.

(Press Q to exit cfdisk)

 cfdisk (util-linux 2.20.1)


                              Disk Drive: /dev/sda
                       Size: 500107862016 bytes, 500.1 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 60801


    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1                    Primary   vfat           [DellUtility]        41.13 
                                      Unusable                             0.82*
    sda2        Boot        Primary   ntfs             [RECOVERY]      13151.25*
    sda3                    Primary   ntfs             [OS]           459418.38*
                            Logical   Free Space                           0.53*
    sda5        NC          Logical   ext4                             23202.90*
    sda6        NC          Logical   swap                              4291.83*
                            Logical   Free Space                           1.08*








     [ Bootable ]  [  Delete  ]  [   Help   ]  [ Maximize ]  [  Print   ]
     [   Quit   ]  [   Type   ]  [  Units   ]  [  Write   ]
                               
                 Toggle bootable flag of the current partition

---

