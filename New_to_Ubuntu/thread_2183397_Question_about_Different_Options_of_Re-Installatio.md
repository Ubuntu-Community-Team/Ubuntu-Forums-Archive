---
title: "Question about Different Options of Re-Installation of Ubuntu 13.10"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by John_Tabor on 2013-10-24
Hi I recently corrupted my Ubuntu 13.10 a few days after downloading it ( dumb me installing stuff wrong ). The OS wont even load now and comes up with an error and it already had a huge problem with it beforehand ( it wouldn't load the Unity desktop after installing Cinnamon ), and so I'm just going to try and re-install it somehow. 

I'm using a USB drive formated to hold the Ubuntu 13.10 image right now and I want to re-install Ubuntu and get rid of the old one. I know there's a partitioning option but I don't really know how to use it. I looked up Ubuntu's re-installation mini guide and it said to set the root of the new partition to /, but I don't know what type of partition to make it. 

On the other hand, if I choose the "Install Ubuntu and erase Disc" option, Does it delete BIOS too? ( This computer had Windows 8 on it before Ubuntu ). I don't want to do it if it does. Also, there's a LVM option when choosing this option that makes it sound like you can make a partition. Does the LVM option actually allow this? Please help. Thanks

---

### Post by John_Tabor on 2013-10-24
please help

---

### Post by scottbomb on 2013-10-24
Type should be ext4. The easiest way is to allow the installer to just erase the previous installation and re-install. It should give that option. But if you partition it yourself, select the partition you want, make it ext4, check the box to format it and mount it as / .

Leave LVM alone. Read about it later if you like, but it's not needed.

---

