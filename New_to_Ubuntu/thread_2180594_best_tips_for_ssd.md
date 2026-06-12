---
title: "best tips for ssd?"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by mreyna16 on 2013-10-13
i have a samsung series 5 ultra laptop, which comes with a 500gb hdd (if im not wrong) with a 25 gb ssd and came with windows 8 installed. Ive been running it with ubuntu 13.04 dualbooted but coming this 17th im gonna download 13.10 and install it in the whole 500gb drive (unless recomended otherwise). What i basically wanna know is if theres any tips u guys can give me to use the ssd to enhance/optimize the performance of ubuntu and why you guys think its the best option... ive seen a cpl of threads on tips but im undecided as to what route to go, any help/tips are appreciated! thanks in advance!

---

### Post by oldfred on 2013-10-13
That sounds like an Ultrabook. 
If totally erasing Windows which I do not suggest but several have done it, you can install / (root) into SSD. Then your system files that are used the most are on the fastest drive. I have a desktop with a 60GB SSD split into two / partitions, one current and one future or test install. Then I have all data on hard drive in data partitions.

Some systems have UEFI that do not fully comply with standards. Those may need Windows to fix or work correctly. 

 Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)



        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
      
 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

 Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
      
  HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
Do not understand why flash cache is required, just install to SSD?
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

---

