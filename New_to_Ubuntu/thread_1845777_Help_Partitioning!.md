---
title: "Help Partitioning!"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by Thrashrokz33 on 2011-09-17
Ok, so I'm in a bit of a pickle here. My 150gb external HDD was currently formatted with 80gb for Windows Vista FAT32, and 60gb for Ubuntu. I figured I'd just be able to delete the ubuntu partition, and extend the Windows one. However, when I deleted the Ubuntu partition inside of the windows partition editor, it created an extended partition. Now, I cannot delete this extended partition at all. When I go to delete it, it says "there is not enough space available on the disk (s) to complete this operation." 

So, I tried booting from the Ubuntu Live CD and using Gparted, but there was no delete option at all for this extended volume. I don't understand exactly what an extended volume is, but shouldn't I just be able to delete it and add that 60gb of space to unallocated memory, and then extend my windows partition to the full 150gb? I'm at a loss for words here.

---

### Post by magic8ball on 2011-09-17
If the partition that you're trying to manipulate is locked, you may need to turn swap off to unlock it.  In Gparted, right-click on the swap space and select "swapoff".  Then see if you can do what you want.  Good luck.

---

### Post by JC Cheloven on 2011-09-17
Please, from a live session opna a terminal and run ```
sudo fdisk -l
``` and post back the output.

---

### Post by Thrashrokz33 on 2011-09-17
This is what I get:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d3fb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29104   233774080    7  HPFS/NTFS
/dev/sda3           29881       30395     4125697    5  Extended
/dev/sda5           29881       30395     4125696   82  Linux swap / Solaris

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1       10804    86777651    c  W95 FAT32 (LBA)
/dev/sdf2           10804       19458    69512193    5  Extended
/dev/sdf5           18944       19458     4124672   82  Linux swap / Solaris

---

### Post by varunendra on 2011-09-18
> **Thrashrokz33 said:**
> This is what I get:

Disk /dev/sda: 250.0 GB, 250000000000 bytes
<snip>
/dev/[COLOR=Red]**sda5**[/COLOR]           29881       30395     4125696   82  [COLOR=Red]**Linux swap**[/COLOR] / Solaris

Disk /dev/sdf: 160.0 GB, 160041885696 bytes
<snip>
/dev/[COLOR=Red]**sdf5**[/COLOR]           18944       19458     4124672   82  [COLOR=Red]**Linux swap**[/COLOR] / Solaris
'5th' or higher partitions are logical partitions 'inside' an extended partition, and you can not delete an extended partition unless you delete all logical partitions 'in' it. So the case seems what *magic8ball* pointed out. Do as he suggested.

---

