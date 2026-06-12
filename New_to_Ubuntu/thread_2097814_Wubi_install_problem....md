---
title: "Wubi install problem..."
date: 2012-12-24
forum: New to Ubuntu
---

### Post by Fred A on 2012-12-24
Hi everyone,
I just purchased an new HP ENVYdv7 laptop (Costco special!!) with windows 8 already installed on it (AMD processor, 8GB RAM, 750GB HD, 64 bit OS). I wanted to try running Ubuntu on this machine, so I downloaded Wubi.exe (build 273) and tried installing Ubuntu 12.10. After downloading, extracting, and installing wubi, came time to reboot the device. However, windows interrupted the reboot, installing its own application updates. So i installed wubi a second time. Installation seemed to go well, and I got the windows dual boot options allowing me to select Windows or Ubuntu. Selecting the windows partition works correctly, but, if I select the Ubuntu partition, I get an error message from the windows boot manager stating that the file (\ubuntu\winboot\wbuilder.mbr) is missing or contains an error. It also gives me a status of 0xC000007B. Whatever that might mean.
Has anyone else seen this problem or has a work around?
Thanks,
Fred

---

### Post by oldfred on 2012-12-24
Welcome to the forums.

I do not know wubi well, but it was posted in another thread that wubi does not work with drives with the new gpt partitioning. And if Windows 8 is preinstalled you have the new UEFI secure boot and gpt partitioning.

Because gpt partitions do not have the 4 primary partition limit it is somewhat easier to create the separate partitions that Ubuntu needs. But the UEFI secure boot has complicated the grub install process to get Ubuntu to work.

If you want to try a partitioned install, you do need to turn secure boot off in UEFI/BIOS, but boot Ubuntu install media DVD or flash in UEFI mode not legacy BIOS mode. You also need to turn off fast boot, quick boot or whatever.

Use Windows MMC to shrink Windows and reboot a couple of times to make sure it runs chkdsk or other repairs it needs on a resize. Back up efi partition and Windows partitions. Best to also make a Windows repair flash drive.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
       Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    
       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    
Some with HP have had issues figuring out what keys to use to get into UEFI/BIOS.
       UEFI/BIOS Boot keys - about halfway down on this page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

    
This is HP desktop, but maybe UEFI/BIOS is similar:
       HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

---

### Post by Fred A on 2012-12-24
Thank you for your reply. My laptop did not come with a recovery DVD, and I am concerned that I might damage the windows partition going this route as it seems a bit complicated.
Do you know if installing Ubuntu from a DVD / USB will have the same problem?

---

### Post by oldfred on 2012-12-24
Someone posted that DVD did not work for their system. Flash is also a bit faster.

I do not know if this works with UEFI or not. You would need one flash to install from and one to install to.

       HOW TO Avoid Wubi & Install Ubuntu on USB Drive -
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

---

