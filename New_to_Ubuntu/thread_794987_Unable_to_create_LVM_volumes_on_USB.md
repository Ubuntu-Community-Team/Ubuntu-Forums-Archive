---
title: "Unable to create LVM volumes on USB"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by drao on 2008-05-15
I tried to create LVM volume on my 2gb usb pen drive. i have done with created the primary partition but when i tried to write the partition table on to drive, i got warning saying that unable to write with error number 22, and sync done...etc. I  searched in net, as per inputs from net, i rebooted my pc and tried to write it. But it same situation as earlier(as in b4 reboot). What would be the problem you ppl guess??

---

### Post by drao on 2008-05-15
One more doubt, Will it work on 2 usb drives? Theoretical what we suppose to achieve from LVM?

---

### Post by drao on 2008-05-15
This is message when i tried to create LVM on USB drive. Details of queary u can find in my eariler posts.

Command (m for help): p

Disk /dev/sdb1: 2050 MB, 2050998272 bytes
64 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Disk identifier: 0x6f20736b

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1               1        1009     2001825   8e  Linux LVM

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.


But after reboot also its not taking new partition table. Can you please point me out any thing wrong ??

---

