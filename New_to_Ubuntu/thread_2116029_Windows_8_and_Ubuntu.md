---
title: "Windows 8 and Ubuntu?"
date: 2013-02-14
forum: New to Ubuntu
---

### Post by Badouken on 2013-02-14
Sorry noob alert here but I want your opinion on this guys! 
I have a new windows 8 computer that has 1TB harddrive now do I partition that drive and say give it something like 120GB to install the OS on and have a place to keep some files or should I have a smaller partition that's like 25GB for the os and then another partition say 80gb for files? What should I do?

More info : windows 8 64bit preinstalled
12Gb of ram! 

Any way to dual boot these / easiest way to do so with Windows 8 already on the harddrive!?

---

### Post by offgridguy on 2013-02-14
I really don't have personal experience, dual booting with the new UEFI mode, but there is
a recent how to here.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2013-02-14
I do multiple installs, so every install is in 25GB including my /home but /home only has my hidden settings. All data is in shared NTFS (from when doing XP) and most new data in a Linux formatted partition. So I suggest smaller / (root).

But it depends on what you want to do and how much space you are willing to allocate.

Do shrink Windows from Windows disk tools and do a full backup of Windows & the efi partition. Do not create new partitions with Windows.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

