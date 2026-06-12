---
title: "New FAT32 partition"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by muldengold on 2008-04-22
Hi,

I want to create a partition for shared windows and Linux files. For this I want to shrink the NTFS windows partition and create a new FAT32 partition using Partition Magic. Browsing this forum I read that people frequently encountered problems with Grub boot loader errors after tampering about with Partition magic. Is there a fool proof way to do it? 

Thanks!

---

### Post by Sef on 2008-04-22
Use [GParted]("http://gparted.sourceforge.net/livecd.php").   It is a graphical partitioner, and no cost to download.  As you mentioned PM and Linux do not always get along well.

---

### Post by mattywarr on 2008-04-22
I was looking to do a similar thing yesterday. I didn't trust the Partition magic from Windows so did it from within the Linux environment - much safer!

I had to boot to the live CD (I only have one disk and all my partitions were mounted - you can;t mess with mounted partitions) and go to System > Administration > Partition Editor/Manager (Forget which) and you can fiddle with partitions there - the interface is very similar to Partition  Magic too.

---

### Post by muldengold on 2008-04-22
Thanks everyone - this forum is great - it usually doesn't take longer than 5mins to get constructive help!

---

### Post by kansasnoob on 2008-04-22
Use GParted!

---

### Post by kansasnoob on 2008-04-22
Check out these tutorials:

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

You'll be glad you did!

I haven't used any of the Vista tuts but the XP tuts work perfectly going both ways, and the "Ubuntu first" tut is a good lesson in GRUB and partitioning.

---

