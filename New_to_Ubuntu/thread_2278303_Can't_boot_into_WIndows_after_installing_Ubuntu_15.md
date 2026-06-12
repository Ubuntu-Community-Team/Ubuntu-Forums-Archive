---
title: "Can't boot into WIndows after installing Ubuntu 15.04"
date: 2015-05-15
forum: New to Ubuntu
---

### Post by konrad9 on 2015-05-15
When I go into GRUB and choose Windows the screen goes black for 1 second or so and then it goes back to GRUB screen and it lets me start only Ubuntu. Help me please.

Boot-repair didn't help : 
[http://paste.ubuntu.com/11146405/](http://paste.ubuntu.com/11146405/)

---

### Post by grahammechanical on 2015-05-15
This could be a clue:

> grub-install: warning: Sector 32 is already in use by the program `FlexNet'; avoiding it.  
This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.

I have no idea what it means or what to do about it. Grub has detected the Windows boot loader and it is looking in the right place for the Windows boot files so Windows should load. Perhaps this is the problem:

>  Boot files:        /boot.ini /ntldr /NTDETECT.COM

I am not familiar with XP boot files but is that enough to do the job?

Regards.

---

### Post by oldfred on 2015-05-15
Flexnet used to be an issue where it & grub wrote to the same sector. But grub created a work around, so not an issue anymore.

But you can never install grub to a NTFS partition. But you can use testdisk to restore from backup. It can also create a new BS with an XP type boot sector.

```
 sda1: ______________________________________

       File system: [COLOR=#ff0000]      ntfs[/COLOR]
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda1 
                       and looks at sector 481629504 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       for (,msdos6)/boot/grub. No errors found in the Boot 
                       Parameter Block.


```

 You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

