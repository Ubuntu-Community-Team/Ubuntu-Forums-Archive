---
title: "moving operating system"
date: 2013-12-25
forum: New to Ubuntu
---

### Post by michaelerdis on 2013-12-25
Good Morning Guys,
I would like to move my ubuntu 12.1 from a 320gb hard drive to a new 2nd 64gb ssd drive. 
Where would I find this info.
Thank you,
Michael

---

### Post by overdrank on 2013-12-25
> **michaelerdis said:**
> Good Morning Guys,
I would like to move my ubuntu 12.1 from a 320gb hard drive to a new 2nd 64gb ssd drive. 
Where would I find this info.
Thank you,
Michael

Hi and welcome, maybe this link can help [_MovingLinuxPartition_]("https://help.ubuntu.com/community/MovingLinuxPartition")

---

### Post by Mark Phelps on 2013-12-25
> from a 320gb hard drive to a new 2nd 64gb ssd drive Since you obviously can't fit 320GB onto 64GB, you won't be able to "clone" your drive to the SSD.  What you need to do first is move data files out of the Ubuntu drive onto an external drive -- and keep doing that until you have less than 64GB left in the Ubuntu partition.

What you can do then is use "clonezilla" to clone the old drive onto the new SSD -- but you will need both connected to do that.

---

### Post by tgalati4 on 2013-12-25
I would simply perform a fresh install on the SSD and keep the 320 GB drive connected as a data backup.  Then pull data from the spinner to the SSD only as you need it.  After a while, you can wipe the 320 GB drive and repurpose it.  You also have the advantage of dual-booting if you have problems with your SSD in the first year.

---

### Post by oldfred on 2013-12-25
+1 on tgalati4's suggestion of clean install.

Plus 12.10 will expire next April anyway.

You only have /home hidden user settings and perhaps some settings in /etc that you may have made system wide that you need to copy. If you copy system you have to change UUID, edit fstab & reinstall grub anyway. You cannot have a cloned partition with the same UUID mounted twice.

How large is SSD? My SSD is 64GB, but I installed two copies of Ubuntu each in 28GB / (root) partitions, but have all data on rotating drive. 

You also have some configuration settings for an SSD that do need to be different.
       Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization](http://wiki.debian.org/SSDOptimization?action=show&redirect=SSDoptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)

I recent changed from discard in fstab to a cron job, but mine is daily.

 Ubuntu Aims To TRIM SSDs By Default
[http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY](http://www.phoronix.com/scan.php?page=news_item&px=MTUxOTY)
Trim as cron job, also must be ext4
[http://www.howtogeek.com/176978/](http://www.howtogeek.com/176978/)

---

### Post by michaelerdis on 2013-12-29
Thankyou , I reinstalled on the 64gb drive and will use the 320gb drive now as an extra hdd

---

