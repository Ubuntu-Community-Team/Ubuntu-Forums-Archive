---
title: "GRUB Bootloader not defaulted"
date: 2018-01-29
forum: New to Ubuntu
---

### Post by o0landshark0o on 2018-01-29
Hi! I just installed Ubuntu 17.10.1 on my computer. When I installed it, it messed up my Widows 10 copy that was also on my PC. 
I can't load Windows 10, my Puppy Linux copy, or Ubuntu, as my computer still is running winboot. Is there any way to change the boot order from an uninstalled copy of Ubuntu on a flash drive? Thanks!

---

### Post by oldfred on 2018-01-29
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by o0landshark0o on 2018-01-30
Thanks for responding so quick! The URL is [http://paste.ubuntu.com/26492164/](http://paste.ubuntu.com/26492164/)

---

### Post by oldfred on 2018-01-31
Your Ubuntu live installer is promoted to sda, and then internal drive is sdb.
A few systems do that, but it then can confuse things.

I would use Boot-Repair to install grub to MBR of sdb, the internal drive. You did have grub installed to the Linux partition which would never be used. BIOS boots from MBR of drive not PBR - partition boot sector.

If using Windows 10 make sure you have a Windows repair disk as Windows will turn its fast start up back on with updates and then grub will not boot it. You then have to temporarily install a Windows boot loader to MBR to directly boot Windows, turn off fast start up again, and then restore grub.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

      [/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]        
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

