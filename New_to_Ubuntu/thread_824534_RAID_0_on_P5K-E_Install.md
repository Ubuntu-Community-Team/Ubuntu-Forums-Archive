---
title: "RAID 0 on P5K-E Install"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by fepple on 2008-06-10
Hello,

I am trying to install Hardy on to my home PC, which has a 3 disks in software RAID 0.

However, when I boot off the install CD it instead shows 3 separate disk.

I'm using an Asus P5K-E Wifi.  When I install XP I have to slip stream the drivers in for "Intel ICH9 RAID Version 7.5.0." 

How can I load drivers once the install has started?  I guess just modprobe?  Does anyone know what I can get them from?

Very noobish of me not to know but when ever I've installed before its just worked :)

Thanks!
Matt

---

### Post by faktorqm on 2008-06-10
Hello! The Intel ICH9 SATA controller works in IDE and AHCI mode. Unfortunately, this motherboard doesn&#8217;t seem to support true hardware RAID. jmicron raid is FAKEraid. FAKEraid used system resources to function. After turning on the ICH9 RAID in BIOS, then configuring two 320 Gb SATA disks as RAID1 (using Ctrl-H during bootup .. manual doesn&#8217;t document this well), Ubuntu still detected two disks &#8230; from this I&#8217;m assuming that the P5K-E does not have real hardware RAID. Not to worry, I can still use the software RAID provided by the Linux kernel anyway.
This can help you [http://ubuntuforums.org/showthread.php?t=627308](http://ubuntuforums.org/showthread.php?t=627308)
Bye!

---

### Post by fepple on 2008-06-10
I thought the Jmicron controller was for the eSATA connectors and the internal one is Intel?  Either way your right that its a software raid (I was disappointed when I realised this) Edit: I see its actually a fake raid, not a software raid -- didnt realise there was a difference

I'll have a better play with the partitioner next time

---

