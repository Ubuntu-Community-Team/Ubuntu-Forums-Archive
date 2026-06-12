---
title: "live usb - hdd imageing program? Backing up win8 hdd 30gb data"
date: 2014-02-15
forum: New to Ubuntu
---

### Post by metroedged on 2014-02-15
Hello everyone. I am installing ubuntu on my grandmothers laptop since it came with windows 8 (confusing even for me as I'm not a fan of overly-flashy GUI's with lack of usability)

She has literally nothing on it, except for what it came with (which is already full of bloatware, gotta love laptops bought from the store)

It takes up about 30gb.

I have an external USB enclosure for a 3.5" sata HDD I want to put the image on.

I don't care if I need to make the image in windows or in ubuntu, but I can't install ubuntu yet, due to the manufacturer or whoever installed the bloatware not being able to partition it properly, and it's just one partition of 500gb. 

IF there is a way to add a partition without erasing the data from it (since it's 30gb used out of 500) that would work also.

---

### Post by tomearp on 2014-02-15
You may find [this article]("https://help.ubuntu.com/community/DriveImaging") in the Community Help Wiki of interest.

---

### Post by bc.haynes on 2014-02-15
Karmic Koala has not been supported for some time. What I would do is download Ubuntu 12.04 and burn it to a DVD. Then run it on the computer and check it out. (Take the "Try Ubuntu" option when you reach that screen.)This will not disturb the Windows partition unless you decide to install it.

---

### Post by oldfred on 2014-02-16
If system came with Windows 8, then it will be a new UEFI system with gpt partitioning. Or a lot different than the 30+ year old BIOS with MBR partitioning that we have used.

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

I would also make a repair flash drive. Linux tools are very limited on what repairs they can make to Windows.

 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

