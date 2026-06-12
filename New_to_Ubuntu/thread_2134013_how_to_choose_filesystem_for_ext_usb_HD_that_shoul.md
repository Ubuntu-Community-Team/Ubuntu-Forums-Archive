---
title: "how to choose filesystem for ext usb HD that should work both 12.04 and win"
date: 2013-04-09
forum: New to Ubuntu
---

### Post by anisterra on 2013-04-09
Hi,  

I need  to choose a proper filesystem for ext usb HD that can work both 12.04 and win xp .

I am already using this  LG 500G USB 3.0  and I ve set it before as EXT 4 on my old Lucid Lynx, it works fine on every linux but for some days I need that data available from a pc with winxp.  

Which kind of formatting should I choose to go from one system to another?


Thanxs in advance :KS

---

### Post by alphacrucis2 on 2013-04-09
ntfs or you could use fat32/vfat but I believe it doesn't allow files > 4GB

---

### Post by papibe on 2013-04-09
Hi anisterra.

There are tools for accessing ext filesystems from Windows. You can go that route.

If you don't find that good enough, there's no much options than good old NTFS.

Just a thought.
Regards.

---

### Post by pfeiffep on 2013-04-09
I'm using a triple boot scenario - I believe NTFS is the best option for dual data storage
sda       SDD - WIN 7   NTFS
sdb1      HDD 500Gb Ubuntu 12.10   ext4
sdb2      HDD 500Gb Ubuntu 13.04 daily   ext4
sdc        ESATA 1Tb  data storage NTFS
hope this helps

---

### Post by anisterra on 2013-04-09
Thank you all,

 I will at first try to find "tools for accessing ext filesystems from Windows" because ubuntu is my main computer and I will just occasionally plug the hdd to a windows filesystem.
In other case,  I will choose ntfs, and try to make a partition on the ext hdd and then format that partition. 

I will add tagged solved when done.

---

### Post by anisterra on 2013-04-10
Ext2Read  reads ext4 files on xp and I  that solved the problem.

---

