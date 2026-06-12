---
title: "how to disable passphase when booting into ubuntu"
date: 2016-09-22
forum: New to Ubuntu
---

### Post by houmingc on 2016-09-22
chew@alvin-UX32VD:~$ sudo fdisk -l
[sudo] password for alvin: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x4f359092

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 24.0 GB, 24015495168 bytes
255 heads, 63 sectors/track, 2919 cylinders, total 46905264 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x26f2eac0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1    46905263    23452631+  ee  GPT

Disk /dev/mapper/sdb3_crypt: 23.2 GB, 23218618368 bytes
255 heads, 63 sectors/track, 2822 cylinders, total 45348864 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sdb3_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--kylin--vg-root: 19.0 GB, 19025362944 bytes
255 heads, 63 sectors/track, 2313 cylinders, total 37158912 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--kylin--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--kylin--vg-swap_1: 4173 MB, 4173332480 bytes
255 heads, 63 sectors/track, 507 cylinders, total 8151040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--kylin--vg-swap_1 doesn't contain a valid partition table

---

### Post by vasa1 on 2016-09-22
See [https://ubuntuforums.org/showthread.php?t=2337879](https://ubuntuforums.org/showthread.php?t=2337879)

---

