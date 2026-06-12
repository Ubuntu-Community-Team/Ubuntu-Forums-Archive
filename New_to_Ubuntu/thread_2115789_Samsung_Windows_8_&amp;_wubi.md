---
title: "Samsung Windows 8 &amp; wubi"
date: 2013-02-13
forum: New to Ubuntu
---

### Post by boarder428 on 2013-02-13
can I use wubi without any issues to install Ubuntu on a windows 8 machine?  I have a Samsung pc and do not want to brick it.  I just bought it!

---

### Post by oldfred on 2013-02-13
Moved to your own thread. Please do not hijack another thread that is not related.

No wubi does not work with gpt partitioned drives and Windows 8 with UEFI has to have gpt partitioning.

As you have noticed some Samsungs may be bricked, but now it can even be Windows software, so it is a major Samsung issue.
See comments on not just Linux specific.
       Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)
[URL="http://mjg59.dreamwidth.org/"]
[/URL]UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released (then not sure).
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.

    But some seem to have installed.
       If Samsung check model number as some can only be installed in legacy/CSM mode or computer may be bricked.
Kernel updates being released and Samsung needs to update UEFI/BIOS.

       Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

---

### Post by boarder428 on 2013-02-14
thanks for the info, considering my options at this point!

---

### Post by boarder428 on 2013-03-04
Well all this is very confusing.  I would like to install Ubuntu on my samsung but not exactly sure how to go about doing so.  From what I have read I don't think my model is included but it is all very confusing!

---

### Post by oldfred on 2013-03-05
You can do a full install. Partitioning is now easier with gpt than the old MBR with the 4 primary partition limit, but UEFI secure boot has complicated it some. 

Use Windows disk tools to shrink Windows and reboot so it can run chkdsk and other fixes to see its new size.

Back up efi partition and you entire Windows after you have made it smaller.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Other installs that worked.
 Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)

---

### Post by boarder428 on 2013-03-07
thanks for the info, I got some more research ahead of me, I'm not to familiar with the disk tools and processes involved in backing up windows 8 or UEFI partitions yet.  I usually use my Windows Home Server to back up my drives but it too will not back up my windows 8 computer.  Sometimes it think I should of just stayed with windows 7 but I was curious to check out the new OS!

---

### Post by oldfred on 2013-03-07
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)


 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

I think you would have to go to a Windows forum to find out why a Windows server will not work with Windows 8.
      
 [URL="http://www.eightforums.com/"]http://www.eightforums.com/
[http://www.sevenforums.com/](http://www.sevenforums.com/)
[http://www.w7forums.com/](http://www.w7forums.com/)
[/URL]

---

