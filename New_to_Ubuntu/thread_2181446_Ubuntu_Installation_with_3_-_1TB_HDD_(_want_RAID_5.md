---
title: "Ubuntu Installation with 3 - 1TB HDD ( want RAID 5)"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by David_Fraser on 2013-10-17
I'm trying to install Ubuntu Server 12.04.3 on my PC (Acer Aspire M5641 - 2.4 GHz Intel Core 2 Quad, 4 GB RAM). I have installed 3 - 1TB SATA drives and would like to have a RAID 5 Array. Two of the drives are brand new and have nothing on them. The third, however was used in a different system and was formatted with NTFS. I don't care anything about any data that may be on it, but am a bit confused now that I'm at the Partitioning stage. On the Overview Page, my disks are listed as...

SCSI3 (0,0,0) (sda) - 1.0 TB yada yada
SCSI6 (0,0,0) (sdg) - 1.0 YD yada yada
         #1  primary  1.0 TB    ntfs

My question is - How do I get the third drive to be listed like the other two or can I set up RAID 5 anyway?

Please keep in mind that I am extremely new to Ubuntu Server. Any help will be greatly appreciated....

Thanks.

---

### Post by nerdtron on 2013-10-18
Just delete that paritition on the manual partitioning screen. And since you are extremely new, the best way to learn is to immerse yourself with the way how things are setup. Here are good resources. I assume you already know why you want raid 5 and how you want your setup to be. Also be sure to know the difference between the physical drives /dev/sda or /dev/sdb and the disk partitions /dev/sda1 or /dev/sbd1.
[https://help.ubuntu.com/lts/serverguide/advanced-installation.html](https://help.ubuntu.com/lts/serverguide/advanced-installation.html)
[http://www.youtube.com/watch?v=z84oBqOxsD0](http://www.youtube.com/watch?v=z84oBqOxsD0)

---

