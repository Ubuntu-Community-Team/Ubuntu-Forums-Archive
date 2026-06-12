---
title: "sudo fdisk -l"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by aszxcv on 2008-11-12
newbie i just want to know if my sudo fdisk -l looks correct
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       27464   220604548+   7  HPFS/NTFS
/dev/sda2           37910       38913     8064630    7  HPFS/NTFS
/dev/sda3           27465       37909    83899462+   5  Extended
/dev/sda5           27465       37478    80437423+  83  Linux
/dev/sda6           37479       37909     3461976   82  Linux swap / Solaris

Partition table entries are not in disk order
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 1973 MB, 1973420032 bytes
32 heads, 32 sectors/track, 941 cylinders
Units = cylinders of 1024 * 2048 = 2097152 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         941     1927104    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 0, 32) logical=(0, 1, 1)

---

### Post by nhasian on 2008-11-12
looks good to me.

---

