---
title: "Dual boot: Win 8.1 won't boot"
date: 2014-02-26
forum: New to Ubuntu
---

### Post by David_G._Smith on 2014-02-26
Hi, I installed Ubuntu 13.10 for the first time, running in a partition alongside Windows 8.1. The Grub menu comes up and Ubuntu boots fine. I have the option on the screen to load Windows 8.1, but when I select it, all I get is a gray screen and a blinking curser in the upper left. I tried Boot-Repair, to no avail, using the reccommended button.  Here is the result: [http://paste.ubuntu.com/6997965/](http://paste.ubuntu.com/6997965/) Please help!

---

### Post by oldfred on 2014-02-26
Windows installs all of its boot files into the one NTFS partition with the boot flag or active partition. And that NTFS partition has to have its own boot code in the PBR or partition boot sector. But you installed grub to the PBR, so Windows is missing essential boot code.

```
 [COLOR=#ff0000]sda1[/COLOR]: _________________________________________

       File system:       [COLOR=#ff0000]ntfs[/COLOR]
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda1 and looks at sector 434044368 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


```

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

Or Similar instructions:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by Gordonbp531 on 2014-02-27
What make of computer?
If you invoke the Boot menu at startup (will depend on your make how you do this) you may well see an option for Windows Boot Loader under Ubuntu.
If there is, you can start Windows from there.
I've left my Lenovo just like that, because I only need to boot into Windows very infrequently...

---

### Post by David_G._Smith on 2014-05-03
OK, sorry about the delay.  Thank you so much for your quick response, OLD FRED.  I followed your first link, sourceforge.   When I run testdisk from the terminal, on the sixth screen, the instructions say to choose "Backup BS".  But, I don't have this option.  My options are: QUIT, LIST, REBUILD BS, REPAIR MFT, and DUMP.  Which do I choose?  Incidentally, above that, if this is relevant, it says: Bootsector OK and Backup Bootsector OK.  Thank you again for your help.

---

### Post by oldfred on 2014-05-03
Backup boot sector may be ok, but it should be Windows not grub. And grub technically is ok as a boot sector just not for NTFS.

If it says they are identical then grub was installed twice and your only choice is rebuild BS. That creates a XP style BS and you then have to run Windows chkdsk from a Windows repair disk to finish fix. But with grub in boot sector Windows will not even run chkdsk, so you have to convert to the XP type first.

---

### Post by David_G._Smith on 2014-05-03
Thank you again.  Honestly, there is so much great information in the link you sent me, I don't know where to begin. OK, so I want to re-run testdisk from terminal and hit REBUILD BS on the sixth screen?  If that's right, what happens next?  Thank you.

---

### Post by oldfred on 2014-05-03
That will put an XP NTFS type boot sector in place. I doubt that Windows 8 will work, but it will at least then know it is a NTFS partition and you can run chkdsk from your Windows repair CD or flash drive.

You did make a repair tool for Windows?
       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Some third party Windows tools may have a chkdsk on them. But otherwise you have to purchase a Windows repair CD. Windows does not make it easy for you to repair your system, if its internal f8 does not work. I guess they assume your system will always partially boot.

      
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)


 We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. So make one yourself before you have to pay to get one.
But they do have a free BCD repair tool.

 Repair BCD
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

---

### Post by David_G._Smith on 2014-05-04
This computer started out with Windows 7.  I later upgraded to Windows 8, then 8.1.  I made the recovery discs for Windows 7 that they ask you to burn when you buy the computer.  Will this help me?  Also, I have the recovery discs from my wife's Windows 8 machine.  Would these help at all?  Thank you again.

---

### Post by oldfred on 2014-05-04
If your wife has Windows 8 I would use it to make the repair flash drive as in the links above. Better to use the same version to make repairs. You may be able to run chkdsk from an older version but not sure, Ihave run chkdsk from a Windows 7 repair flash drive on my XP.

My last Windows was XP so not an expert on that. Only picked up on fixes to dual boot with Ubuntu.
Better forum for Windows questions.
       [http://www.eightforums.com/](http://www.eightforums.com/)

---

