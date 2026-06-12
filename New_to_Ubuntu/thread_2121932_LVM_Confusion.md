---
title: "LVM Confusion"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by kermtfrg on 2013-03-03
I think I screwed up somewhere along the way in setting up my lvm and I don't know how to fix it.
 
Background:  I'm migrating from Windows Home Server to Ubuntu Server.  I bought a new 2TB hard drive and created the LVM using all of it and began copying all of the data from windows to ubuntu.  I got about halfway thru and was able to remove a 2TB  hard drive from windows and added it to the LVM so I could finish copying.  The copy completed and I took the final 2TB and a 3TB drive and tried to add them to the lvm.  It looks like they are there.  The logical shows a total size of around 9TB.  Nemo shows my total capacity as 4.8TB with 3.3TB used.  The physical volumes sdc1, sdc2 and sdg were added after I got all of that data copied over.  I must have done something wrong when I was trying to add them to the logical volume 

```
  PV         VG          Fmt  Attr PSize   PFree  Used     /dev/sda5  mediaserver lvm2 a-   931.27g     0  931.27g
  /dev/sdb1  mediaserver lvm2 a-     1.82t     0    1.82t
  /dev/sdc1  mediaserver lvm2 a-     2.00t     0    2.00t
  /dev/sdc2  mediaserver lvm2 a-   746.62g 17.99g 728.62g
  /dev/sdf1  mediaserver lvm2 a-     1.82t     0    1.82t
  /dev/sdg   mediaserver lvm2 a-     1.82t     0    1.82t

```

```

  --- Logical volume ---
  LV Name                /dev/mediaserver/homeserver
  VG Name                mediaserver
  LV UUID                ax3phG-oLdJ-Dzz6-97Ql-fNX4-5ztk-CKf9Fs
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                8.99 TiB
  Current LE             2356143
  Segments               6
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2

```

I tried to remove one so I could try again but can't do that either:
```

sudo pvmove /dev/sdc2
  No extents available for allocation
```

What can I do to fix this?  I thought about reducing the size of the logical volume so that extents would be available but I'm afraid of losing data.  Is this safe to do?  I installed system-config-lvm and see that it has a nice little slider that allows me to change the size but will I lose any data?

If it helps here is the output of fdisk -l:

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000ae133


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758  1953523711   976510977    5  Extended
Partition 2 does not start on physical sector boundary.
/dev/sda5          501760  1953523711   976510976   8e  Linux LVM


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfc2e3b94


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  3907007999  1953503968+   7  HPFS/NTFS/exFAT
Note: sector size is 4096 (not 512)


Disk /dev/sdc: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4c34717c


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   536844104  2147376168   8e  Linux LVM
/dev/sdc2       536844288   732566527   782888960   83  Linux


Disk /dev/mapper/mediaserver-root: 93.6 GB, 93591699456 bytes
255 heads, 63 sectors/track, 11378 cylinders, total 182796288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/mediaserver-root doesn't contain a valid partition table


Disk /dev/mapper/mediaserver-swap_1: 6404 MB, 6404702208 bytes
255 heads, 63 sectors/track, 778 cylinders, total 12509184 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/mediaserver-swap_1 doesn't contain a valid partition table


Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa89f29bb


   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1              63  3907007999  1953503968+   7  HPFS/NTFS/exFAT


Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdg doesn't contain a valid partition table
Note: sector size is 4096 (not 512)


Disk /dev/mapper/mediaserver-homeserver: 9882.4 GB, 9882380009472 bytes
255 heads, 63 sectors/track, 150183 cylinders, total 2412690432 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/mediaserver-homeserver doesn't contain a valid partition table

```

---

