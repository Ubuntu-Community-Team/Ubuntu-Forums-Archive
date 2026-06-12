---
title: "reformatting HD after 8.04 to 8.10 upgrade"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by billsimson on 2008-11-15
I have an IBM Thinkpad R31, installed Ubuntu 8.04 - it worked but crashed with firefox - then tried to upgrade to 8.10 now ubuntu only works from the CD  for 8.04 - I ran sudo gparted and got the following.  How do I get rid of all the mounted drives?

Partition	File Sys   Size GB	Used	Unused	Flag
/DEV/SDA1	NTFS	  35.44 GB	9.79	25.66	Boot
/DEV/SDA2	Extended  39.08 GB	--	--	
 /dev/sda5	fat32	  33.47 GB     66.91 MB		
 /dev/sda7	ext3	   3.74 GB 	2.52 GB		
 /dev/sda8	Linux Swap	         235 MB --	--	
 /dev/sda6	Linux Swap	        1.65 GB	--	--	
					
Unable to delete /dev/sd5					
Please  unmount logical partition have a number higher than 5					
(Error the same for all /dev/sda 5-8 partitions the number in the error					
message matches the number in the partition label)

---

### Post by nhasian on 2008-11-15
if you boot off the liveCD you can just delete the partitions you dont want and resize the partitions you want to keep with Gparted.

---

### Post by Keen101 on 2008-11-15
Yeah either use gparted from the ubuntu live-cd or get this. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by billsimson on 2008-11-17
Thanks I down loaded gparted and made a bootable CD, reformated and it seemed to work after reloading 8.04, however when booting from the hard drive the following is presented:

-------------------------------------------------
Ubuntu 8.04.01 Kernel  2.6.24-21 Generic
Ubuntu 8.04.01 Kernel  2.6.24-21 (Recovery Mode)
Ubuntu 8.04.01 Kernel  2.6.24-16 Generic
Ubuntu 8.04.01 Kernel  2.6.24-16 (Recovery Mode)
8.04.1 Memtest06+
Other Operating Systems:
Microsoft Windows XP Home Edition
--------------------------------------------
Both Kernel Generic modes work, but what does this mean?  There is only one Ubuntu partition and one linux-swap partition.

Thanks for you help - I look forward to your response and hope Firefox doesn't crash as I submitted previously.

Bill Simson

---

