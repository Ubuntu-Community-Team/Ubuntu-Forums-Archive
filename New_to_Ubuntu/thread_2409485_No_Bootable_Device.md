---
title: "No Bootable Device"
date: 2019-01-02
forum: New to Ubuntu
---

### Post by ScottyP431 on 2019-01-02
I just installed Ubuntu to dual boot with windows 10 on my old laptop. Ubuntu ran fine, I restarted and it booted right to windows which worked fine. Then I realized it never gave me the option to pick which OS I wanted at start up, so I restarted to see if I missed it and from then on its been giving me the "No Boot Device Found. Press any key to reboot the machine" 

The laptop is an Alienware Mx17, I saw some other people have had a similar problem but the solutions were specific to Acer laptops/my bios doesn't have the same options. 

The bios boot menu currently looks like this

[ATTACH=CONFIG]282083[/ATTACH]

Thanks!

---

### Post by oldfred on 2019-01-02
have you updated UEFI from Alienware?
Many of issues of Dell are similar or the same as Alienware systems.

This may be same UEFI?
       Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

Some of these are now older, and issues should be less.

 Alienware Area 51 R4 16.04 UEFI update
[https://ubuntuforums.org/showthread.php?t=2397456](https://ubuntuforums.org/showthread.php?t=2397456)
[https://askubuntu.com/questions/1085884/install-ubuntu-on-alienware-15-r4](https://askubuntu.com/questions/1085884/install-ubuntu-on-alienware-15-r4)
Ubuntu 15.10 Dual Boot Win 10 Alienware 15 R2 Problem 
[http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555](http://ubuntuforums.org/showthread.php?t=2311390&p=13430555#post13430555)
[http://ubuntuforums.org/showthread.php?t=2313054](http://ubuntuforums.org/showthread.php?t=2313054)
[URL="http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr"]http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr

      [/URL] May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the summary report ( not post full report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    [URL="http://askubuntu.com/questions/795755/grub-problems-on-dual-boot-windows-10-ubuntu-16-04-laptop-using-samsung-950-pr"]
[/URL]

---

### Post by ScottyP431 on 2019-01-03
Here is the link to the summary- [http://paste.ubuntu.com/p/Nrm8H25rsv/](http://paste.ubuntu.com/p/Nrm8H25rsv/)

I am working my way through the UEFI links to see if any of that works- thanks for the suggestions

---

### Post by yancek on 2019-01-03
Your boot repair output shows that you have windows partitions on both drives.  Which one has the OS, is it sda with the 3 windows partitions or sdb with only one windows partition?  Guessing sda?  You have Ubuntu installed on sdb and the Ubuntu Grub boot code is installed to the MBR of sda and windows code to the MBR of sdb.  Which drive (sda or sdb) is set to first boot priority in the BIOS?  If you change the priority, does this resolve your boot problems?  

Your boot repair output shows you have a Legacy install rather than UEFI.  Is this an upgrade from windows 7?  Turn off Secure Boot in the BIOS as recommended in boot repair.  Try changing the boot priority for the drives and reboot.  If that fails, turn off Fast Boot in the BIOS (shown in the image in your initial post) and run boot repair again and you should not then see the 'resource busy' warnings on the windows partitions.

---

### Post by oldfred on 2019-01-03
Do not run any auto fix with Boot-Repair.
That installs grub to the MBR of all drives. You really want Windows boot loader in MBR of sda and grub in the MBR of sdb and BIOS set to boot sdb first.

Windows 8 or 10 also has fast start up which turns on hibernation flag. Then the Linux NTFS driver will not mount any NTFS partitions to prevent damage to the hibernated files. Make sure fast start up is off in Windows. If you put a Windows boot loader back into sda using your Windows repair disk (fixMBR command). Not sure Boot-Repair will install the syslinux boot loader which works like Windows boot loader to sda, unless it can correctly see the NTFS partition with boot files.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

