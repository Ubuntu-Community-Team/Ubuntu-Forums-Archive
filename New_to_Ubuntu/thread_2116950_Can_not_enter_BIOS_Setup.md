---
title: "Can not enter BIOS Setup"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2013-02-17
Hi friends.
 
This week I bought a DELL inspirion 14R 5420. I want to install Ubuntu along with Windows 8. But here are problems:
 
1) Dell Factory Reset Partition is corrupt. When I contacted Dell, I was sent Windows 8 DVD so that if in future I face any problem I will be able to install windows 8 again.
 
2) From yesterday I can not enter BIOS in any way. F2 is key to enter BIOS but pressing F2 has no effect and system load windows 8. F12 is for boot options but that too dose not offer any boot options and load Windows 8. [ Both F12 and F2 worked perfectly till yesterday ]
 
3) Shift + restart offers trouble shooting options like Boot Menu, Setup, Change Boot Mode but these options too fails to load BIOS. The only option that is working currently is Booting through Windows DVD.
 
4) I have already tried removing Laptop Battery but that did not helped.
 
Please help me correct the problem. What will happen if I format entire hard disk ( including EFI partition ). I do not have much idea about EFI partition. Is it possible to recreate EFI Partition with windows 8 DVD?

---

### Post by sujitrjadhav on 2013-02-17
Flashing BIOS solved the problem

---

### Post by oldfred on 2013-02-17
You should backup efi partition and your full Windows install.

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

    You will need to install Ubuntu in UEFI mode. And turn off secure boot.
Also turn off fast boot as that may have been your issue with not getting into UEFI/BIOS. Some systems only get into UEFI menus from Windows entry when fast boot is on.
       
You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)
    
       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

