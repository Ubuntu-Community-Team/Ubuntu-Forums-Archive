---
title: "Reformat external drive used with XP for use with Ubuntu"
date: 2014-09-04
forum: New to Ubuntu
---

### Post by rod52 on 2014-09-04
Before I install Ubuntu, I have an external USB hard drive used with Windows XP.  I assume I need to reformat it for use with Ubuntu.  Do I leave it connected when I install Ubuntu, or reformat it after I install Ubuntu?

---

### Post by Mark Phelps on 2014-09-04
Leave it disconnected when you install Ubuntu.  This prevents accidental installation of boot loader files to the wrong drive.

You can always connect the drive after Ubuntu install and use Gparted to reformat it.

---

### Post by rod52 on 2014-09-04
Thank you.

---

### Post by Rob Sayer on 2014-09-04
I've never reformatted an external USB data drive for linux use.  Linux understands the formats used by windows just fine.  The reverse isn't true.  If you have an external HD formatted to EXT4 (the default in ubuntu) windows won't be able to read it.  It'll think it's unallocated space.

---

### Post by Mike_Walsh on 2014-09-04
Depending on the size of your drive, and what you want to use it for, you could do as I have done.

I have a 500 Gb Seagate USB external HDD. I have the first partition, sdb1, formatted to NTFS (approx 200 Gb.) The remainder of the drive is formatted to ext 4, as I have an extended partition (sdb4), and half-a-dozen different Linux distros installed into smaller logical partitions ( sdb5-10)

This gives you a good chunk of space for Windows apps to recognise for THEIR use; and Linux can read the whole thing anyway.

Job done.

Regards,

Mike.

---

### Post by jvcastle on 2014-09-04
Most of the time whatever format an external drive came with works fine with windows or linux  - unless you have large raw video files or backups > 2Gb.  I find formatting my external drives to NTFS the most useful since both OSes can read the drive.  With linux-specific formats like ext4 means whatever is there can't be (easily) read by windows.

---

### Post by mastablasta on 2014-09-05
another potential issue of leaving external drive in NTFS is that Ubuntu can't fix the file system errors on that drive. only windows or windows tools can do that. 

solution - have a windows rescue CD ready with relevant tools (e.g. chkdsk ...)

since I also use windows at home I never formatted the external hard drives (i.e. I left it as NTFS) so that both systems can use it.

---

