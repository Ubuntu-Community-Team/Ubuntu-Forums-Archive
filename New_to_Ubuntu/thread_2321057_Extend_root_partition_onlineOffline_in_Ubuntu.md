---
title: "Extend root partition online/Offline in Ubuntu"
date: 2016-04-20
forum: New to Ubuntu
---

### Post by rohithroki on 2016-04-20
Dear Team,

I am using Ubuntu 12.04.5 LTS and my root partition (normal partition not an LVM) is 90% Utilized.

Disk /dev/sda: 483.2 GB, 483183820800 bytes
255 heads, 63 sectors/track, 58743 cylinders, total 943718400 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022bc0   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   898437499   449217726   83  Linux
/dev/sda2       898437500   943718399    22640450   82  Linux swap / Solaris

Is there a way where I can extend my root partition online/Offline.If yes kindly share me the detailed steps on how to proceed further.

Regards,
RKJ

---

### Post by Impavidus on 2016-04-20
Your harddrive is full. You could make the swap partition a bit smaller perhaps, as it is rather large, and add the space to your root partition, but your root partition would still be 88% full. Maybe you can add another hard drive, format it, mount the partitions somewhere convenient and move data over to the new drive.

Partitions can only be resized offline. In case of the root partition, you have to do it while running from a live disk.

---

### Post by grahammechanical on 2016-04-20
> Is there a way where I can extend my root partition online/Offline.

If this means what I think it means, then you should be looking at cloud storage. Or even Ubuntu on Cloud. Which I do not really think you mean

[URL="http://www.ubuntu.com/cloud"]http://www.ubuntu.com/cloud

[/URL]Basically, you need more storage space. Larger hard drives or Cloud storage.

Regards.

---

