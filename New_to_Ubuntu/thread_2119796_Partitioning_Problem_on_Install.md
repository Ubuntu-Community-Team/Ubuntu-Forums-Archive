---
title: "Partitioning Problem on Install"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by harryedgeworth on 2013-02-24
Hi folks, 

I'm having this problem when installing Ubuntu 12.10 Secure Remix. 

When I get to the partition screen, I get the two OS' (Win8) and Ubuntu. However the two sections only have the drive space written in them, and it doesn't indicate which section refers to which OS. I only want to give Ubuntu 90GB, and then give Win8 the rest. Which one is Ubuntu? The left or the right? 

I've tried to use the advanced partioning tool, but it is too complicated for my liking, and I only want to use the simple tool as shown in the picture

[IMG]http://i48.tinypic.com/34of0b5.jpg[/IMG]

Thanks in advance.

---

### Post by zrdc28 on 2013-02-24
I am not sure about win8 but if you were on vista or win7 you might be going about it wrong. On either of the two above you need to do your particians from within the windows system first. I don't remember exactly
how it is done but there are many articles on google on how to do it for win7 & vista and maybe win8. Look at the link below and it might get you what you want.


[http://www.youtube.com/watch?v=wNCSbTyUzoM](http://www.youtube.com/watch?v=wNCSbTyUzoM)

---

### Post by JLeon85 on 2013-02-24
Go to "My Computer" in Win 8 and you'll see the total size of the partition that 8 is installed on. The other one should be safe to install Ubuntu on.

---

### Post by oldfred on 2013-02-25
Always best to use Windows to shrink the Windows partition to the size you want and leave the rest unallocated for Ubuntu install. Do not use Windows to create new partitions as it cannot create Linux formatted partitions and may convert to dynamic which can be a huge issue.
Then reboot Windows before installing Ubuntu, so it can run it fixes including chkdsk that it has to do on a partition resize.

What computer is this? 
Some Windows 8 systems have major issues with UEFI dual booting, other work reasonably well but all require at least a few fixes.

Also backup efi partition as well as main Windows install after you have shrunk it. 
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

    
       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

