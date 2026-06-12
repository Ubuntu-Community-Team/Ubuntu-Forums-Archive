---
title: "Reading Linux Filesystem from Windows"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by uho on 2008-11-02
So, I'm dual booting ubuntu 8.10 and windows xp pro, but how can I access my files from ubuntu. Is there away to enable ext3 capabilities in windows?

---

### Post by brandoncolorado on 2008-11-02
[http://lifehacker.com/software/ubuntu/ubuntu-tip--how-to-mount-a-windows-ntfs-partition-203102.php](http://lifehacker.com/software/ubuntu/ubuntu-tip--how-to-mount-a-windows-ntfs-partition-203102.php)

That helpful?

---

### Post by CLVPX on 2008-11-02
If your XP partition is NTFS ( I assume so ) or FAT32 then you can access the drive straight from ubuntu by mounting, or if you insist on accessing ubuntu from windows;

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

This looks like the easiest option as far as I can see, windows does not support ext3 without 3rd party software such as this.

---

### Post by blue13130 on 2008-11-02
I use Ext2 IFS for Windows to access my linux partitions.  It can read ext2 and ext3 partitions.

Here is the link to the website
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

