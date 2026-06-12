---
title: "Boot Windows Partition?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by mbstrlbstr on 2008-10-29
After a while away from Ubuntu (since Dapper Drake) I am please to see all the visual effects working nicely without any tweaking to .xorg. But I can't figure out how to mount my windows partition, so I can listen to music and view my pictures. Here are my fstab results:

```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2               9        1314    10485760    7  HPFS/NTFS
/dev/sda3   *        1314       14267   104047612    7  HPFS/NTFS
/dev/sda4           14267       14594     2621440    f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown

```

---

### Post by Duck2006 on 2008-10-29
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by mbstrlbstr on 2008-10-29
I looked at doing this, but the partition that all of my stuff is on, isn't showing. Just the recovery and the "Dell media direct". Can you tell me how to mount the sda3 partition found in my fstab?

---

### Post by Duck2006 on 2008-10-29
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

