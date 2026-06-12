---
title: "$logFile Problem"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by rmx on 2008-08-21
Hi.

I have a double boot ubuntu 8.04/ XP.
the thing is that the I erased some systems files from XP and I don't have the CD.
i have a backup on an external drive.
so Everything would be ok if ubuntu let me mount my xp drive.

The problem is that I can't mount windows drive because $LogFile indicates unclean shutdown (0, 0) and NTFS is marked to be in use.
I tried to mount using: 
   sudo mount -t ntfs-3g /dev/sda1 /media/windows -o remove_hiberfile
   sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force
And I added to fstab the following line
   /dev/sda1 /media/windows ntfs-3g force 0 0

I can't boot windows, so I can't make a clean shutdown.

Is there a way to clear this $logfile?? 

Thanks

Rmx

---

