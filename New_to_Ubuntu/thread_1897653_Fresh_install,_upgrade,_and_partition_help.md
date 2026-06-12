---
title: "Fresh install, upgrade, and partition help"
date: 2011-12-19
forum: New to Ubuntu
---

### Post by 40FiveSeventy on 2011-12-19
Alright all, attached herein (I hope) is my output for the [ sudo fdisk -l ] string.

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2              13        1318    10485760    7  HPFS/NTFS
/dev/sda3   *        1318       23513   178279693+   7  HPFS/NTFS
/dev/sda4           23513       30402    55333889    f  W95 Ext'd (LBA)
/dev/sda5           30075       30402     2620416   dd  Unknown
/dev/sda6           23513       27410    31305630   83  Linux
/dev/sda7           29802       30075     2192384   82  Linux swap / Solaris
/dev/sda8           27410       29696    18360320   83  Linux
/dev/sda9           29696       29801      845824   82  Linux swap / Solaris

Partition table entries are not in disk order
```Obviously there is some absurdity that has happened. What I would LIKE to do is get a fresh install with JUST ubuntu and some free space at the back in for a windows install at a later date. Is this possible? And is there a best/efficient way to do it?

-45S

---

### Post by bodhi.zazen on 2011-12-19
Lookas as if you installed ubuntu a second time. Boot a live CD, launch gparted and manage your partitions.

If this is a fresh install it may be easeir and faster to delete all the linux partitions and create a swap an / partition to be used by the installer. When you install, use the "Specify partitions manually (Advanced) option.

[img]https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step4a.png[/img]

---

### Post by cortman on 2011-12-19
If your data is backed up, and you do want a fresh installation anyway just create a new partition table when you're re-installing Ubuntu and add an extra NTFS partition.

---

