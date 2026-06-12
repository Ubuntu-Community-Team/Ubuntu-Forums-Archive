---
title: "grub rescue error"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-04-25
Have tried 8 times to install from LiveCD (even downloaded & created a new CD) I repeatedly get the same error on bootup: [B]grub rescue > error: fd0 cannot get C/H/S values.
[/B]Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cc0f2
Here is the partition layout - is it correct?
[U]
[http://ubuntuforums.org/attachment.php?attachmentid=216575&stc=1&d=1335383937](http://ubuntuforums.org/attachment.php?attachmentid=216575&stc=1&d=1335383937)


[/U]

---

### Post by Bumpalot on 2012-04-26
Have solved this - fixed grub (it was pointing to sdd1 which is the extended partition-no folders).

---

