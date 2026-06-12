---
title: "Partitioning question"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by afty on 2008-10-30
I am new to Ubuntu.  In the past I've used Red Hat and Fedora distributions.  I am now trying to install Ubuntu 8.10 on my laptop, and I'm unclear on how the partitioner works.  I want to set up a dual boot with Windows Vista, and I have already shrunk the Vista partition from within Windows.  I have a big chunk of unallocated space, and I want to install Ubuntu there and accept the default partitioning scheme.  However, I can't determine which option in the install corresponds to what I want to do.

From the written descriptions, it seems that I would want to choose "Guided - use the largest contiguous free space."  However, if I select this, the graphic that goes along with this screen shows Ubuntu taking over the whole hard drive and not just the free space.  I've attached a screenshot so you can see what I'm talking about.

If I select this option, will it wipe out my Windows partition as it shows in the graphic, or will it just use the free space?  Is there any way I can see/modify its partitioning decisions before they are written to disk?

---

### Post by aramadia on 2008-10-30
I always use manual partitioning.  Select manual and hit next.

Select the correct partition based on the size.  You should probably see windows as an NTFS partition.  Configure the other partition as an ext3 filesystem (default) and mount it to / (root).

Also if you have little memory, it is recommended to create a "swap" partition.

---

### Post by eternalnewbee on 2008-10-31
Choose Maual and select the partition where you want to install ubuntu and click Edit Partition and then set the partition as / and format ext3.
I have a swap partition of one GB, but you should search a bit deeper for how much swap you need.
Hope this helps.
________________________________
Ubuntu Release 8.10 (intrepid)
Kernel Linux 2.6.7-7
GNOME 2.24.1
AMD Athlon(tm) XP 899.219 MHz 256 KB
GeForce 7300 GT

---

### Post by afty on 2008-10-31
Thanks guys.  Is this a bug in the installer?  Should I report it?

---

