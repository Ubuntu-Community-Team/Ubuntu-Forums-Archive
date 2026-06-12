---
title: "Grub dual boot problem(solved)"
date: 2014-08-13
forum: New to Ubuntu
---

### Post by a.v. on 2014-08-13
Hi, I'm new to ubuntu and I'm really sorry if I break any forum-rules. 
I have a problem starting my second OS.
After installing Win8.1 on my SSD on my w520 I wanted to install Ubuntu. So I shrunk the partition of Win8.1 20480mb and startet installing Ubuntu on that partition. I made the mistake, that I set as "device for boot loader installation" /dev/sda1 Windows8 loader. After trying to boot Win8.1 from grub2 it just restartet. Retrying it and updating grub didn't help. I couldn't figure it out which commands I have to use to solve this problem. I would really be thankfull if you could help me. I'm sure anywhere in the forum there is a solution, but because I am new to Ubuntu I don't understand most oft the explanations, I need commands to copy-paste ;)

cheers
a.v.


edit:solved by deleting everything and installing everything new.

---

### Post by yancek on 2014-08-13
More information will be needed.  If you can boot the installed Ubuntu, go to the site below.  Read the instructions in the link in the Description box on that page, then download and run the script.  It will output a results.txt file which you can post here and someone should be able to help you.  If you can't boot the installed Ubuntu, use the installation medium DVD/flash drive to do it.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by a.v. on 2014-08-13
Thanks a lot, the report is attached.

---

### Post by oldfred on 2014-08-14
You normally do not install grub2's boot loader to a partition and never install it to a NTFS partition as Windows has essential boot code in the partition boot sector or PBR. It does keep a backup and we can use testdisk to restore the Windows PBR. If backup is not valid you will need a Windows repair CD.

```
 sda1: _________________________________

       File system:       [COLOR=#ff0000]ntfs[/COLOR]
    Boot sector type: [COLOR=#ff0000] Grub2[/COLOR] (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sda1 
                       and looks at sector 225432896 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in partition 112 for . No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD


```

Testdisk may say the BS boot sector is ok, but grub installed is valid, just not with NTFS. 

You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)


Then in Ubuntu run this to add Windows to grub boot menu.
sudo update-grub

Also with Windows 8, even in BIOS boot mode:
 WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked

---

