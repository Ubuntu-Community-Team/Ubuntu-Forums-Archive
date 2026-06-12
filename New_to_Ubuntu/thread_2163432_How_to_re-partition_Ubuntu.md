---
title: "How to re-partition Ubuntu"
date: 2013-07-18
forum: New to Ubuntu
---

### Post by Weatherman3040 on 2013-07-18
When I installed Ubuntu, I made the partition too small. How can I fix that? I know I can edit the partition when I boot from the disk, but what partition is Ubuntu on? My other OS is Windows 7. Thanks!

---

### Post by DeathByDenim on 2013-07-18
If you boot from the live-CD, you can indeed change your partitions using GParted. The Windows partition will be of the type NTFS, while the Ubuntu partition will be of the type ext4. Be sure to back up your data first though, since changing partitions can be tricky.

---

### Post by Weatherman3040 on 2013-07-18
Thank You!

---

### Post by Impavidus on 2013-07-18
You may have to shrink your Windows partition before you can expand your Ubuntu partition. Some people have reported problems on Win7 when using gparted for resizing Windows partitions. It may be the savest option to use Windows tools to shrink the Windows partition and then boot from your live disk to expand the Ubuntu partition.

---

### Post by paulee81 on 2013-07-18
Having just gone through installing a dual boot system with Win7, I would have to agree with the comment by Impavidus. If there are any stray clusters on the win partition you may lose them unless you use the win partition manager.

---

### Post by techvish81 on 2013-07-18
backup imp files and defrag your windows partition before doing anything.

---

