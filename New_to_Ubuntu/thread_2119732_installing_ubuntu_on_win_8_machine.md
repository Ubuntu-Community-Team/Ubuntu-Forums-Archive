---
title: "installing ubuntu on win 8 machine"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by j3s3 on 2013-02-24
new to Ubuntu but seriouslu want to try it out.  I have recently purchased a new laptop preinstalled with windows 8, and with great disappointment. so here I am reading up on installing Ubuntu, Can't totally do without windows at least not yet. I have partition my drive to make space for Ubuntu disable fast BOOT and uefi in bios and even downloaded easybcd but haven't tried it yet.  My question is that partition I have created I can only format in ntfs?  will Ubuntu be happy or what am I missing?
thanks
 
J3S3

---

### Post by Branimir on 2013-02-24
Why don;t you just try installation in virtual machine
first? Or perhaps wubi?
If you know what you are doing you can format Ubuntu
partition as ext4, but first you have to know what
you are doing.

---

### Post by kabukiM0n0 on 2013-02-24
Just format it to ext3 while installing Ubuntu. Try it out, have a play around and if you are happy with it - get rid of m$!
At least I think that is what you are asking.

---

### Post by j3s3 on 2013-02-24
ok I am new to all this, how do I format to ext3 ?  I use the win 8 format and it only gives the ntfs option.  There must be something I am doing wrong !  I have Ubuntu on a flash memory stick that is plugged into usb .  Is there some other program I should be using ?
 
Thanks
J3S3

---

### Post by oldfred on 2013-02-24
Wubi does not work with gpt partitions and UEFI required gpt partitioning.

Do not create partitions with Windows, it know nothing about Linux. But do use Windows to shrink the Windows NTFS partition and reboot a couple of times to let it run chkdsk and make other fixes for new size.

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

    
What system is this? A few brands particularly Samsung have issues which you need to be very aware of before installing. Best to fully backup efi partition and your Windows install after shrinking.

       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

      
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by kabukiM0n0 on 2013-02-24
Are you trying to format from inside m$? if so look at oldfred's reponse in this thread /showthread.php?t=2119689

I was referring to once in Ubuntu installation, when you choose your partitions. To go with ext3 over ext4 and continue with the installation.

---

