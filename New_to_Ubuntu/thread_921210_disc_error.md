---
title: "disc error?"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by faraz_k86 on 2008-09-16
k so this is really strange now. 

Im so tired of this message that because of this i had to do a complete system format, reparition and then install my operating systems.

I had linux as well as windows xp on my HDD, During GRUB when i chose linux it started up without any problems, but when i chose windows xp it gave me a "disc error"

why? so like i said i completely formated and am now only trying to install xp, but even now i get a disc error.

**plz help**

---

### Post by faraz_k86 on 2008-09-16
just adding some more info.

I partitioned the HDD using GParted, and for the primary partition i set the flag to boot.

is that right? what other flags should i enable?

---

### Post by cariboo on 2008-09-16
First off, if something doesn't work the way you expect it to, reinstalling is not going to fix the problem, that is the windows way, linux is not windows, you have to change your mindset. If you could post the output of:

```
sudo fdisk -l
```

You will have to do this in a Applications-->Accessoreis-->Terminal, and post the output in your next post.

Jim

---

### Post by faraz_k86 on 2008-09-16
did you mean fdisk -1 or fdisk -l (figures, they both look the same. :/  )

```
sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
mint@mint ~ $ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9fd39fd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3833    30788541    c  W95 FAT32 (LBA)
Partition 1 does not end on cylinder boundary.
/dev/sda2            3834        9729    47359620    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5            3834        5956    17052966    b  W95 FAT32
/dev/sda6            5957        9729    30306591    b  W95 FAT32

Disk /dev/sdb: 4022 MB, 4022337536 bytes
29 heads, 28 sectors/track, 9675 cylinders
Units = cylinders of 812 * 512 = 415744 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9676     3928060    b  W95 FAT32
mint@mint ~ $ 


```

---

### Post by Thanoulis on 2008-09-16
It's fdisk -l (l from *list*) ;)

---

### Post by faraz_k86 on 2008-09-16
yes i figured that out, the report is of fdisk -l

---

### Post by faraz_k86 on 2008-09-16
bump

---

### Post by faraz_k86 on 2008-09-16
im still waiting with the screwed up laptop in front of me.

i noticed that in the report it says

> Partition 1 does not end on cylinder boundary.

does this mean that GParted screwed up in the partitioning process?

---

