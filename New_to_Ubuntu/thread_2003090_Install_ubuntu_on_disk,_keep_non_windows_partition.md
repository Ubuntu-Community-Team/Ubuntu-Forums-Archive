---
title: "Install ubuntu on disk, keep non windows partition"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by Lism on 2012-06-13
Hi guys,

I had a dual boot setup with W7 and Ubuntu but now I want to completely ditch windows and use Ubuntu. Now, my hard disk is currently split into two partitions: Windows and Steam where Steam contains all my games.

I want to install ubuntu on the windows partition and keep the steam partiton as i plan to run steam under wine. 

Im using the live cd to install but when I try to install it tells me that the entire HDD will be used so Im assuming that ill lose 500gb worth of games, I could redownload but my dl speeds are terrible.

Any tips? Thanks

---

### Post by drs305 on 2012-06-13
You can select the 'Do something else' (the bottom of the 3) option which will allow you to select the partition on which you want to install Ubuntu. You will select the partition, select the mountpoint (/) and filesystem type (e.g. ext4) and tick the box to format the partition. Just make sure you have the correct partition selected (check name, size and location).

---

### Post by Mark Phelps on 2012-06-14
> **Lism said:**
> ... I want to install ubuntu on the windows partition ...

Basically ... you can't do that, at least, without reformatting that partition.

Ubuntu will not install to Windows filesystem partitions.  You can do that with Wubi, but then, you said you wanted to be rid of Windows.  So, using Wubi defeats that purpose.

As mentioned, you need to reformat the Windows partition to Ext4.  Then, you can install Ubuntu to it.

---

