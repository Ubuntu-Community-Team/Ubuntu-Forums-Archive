---
title: "Problem in dual boot"
date: 2013-08-31
forum: New to Ubuntu
---

### Post by filipe3 on 2013-08-31
Hi.
I have installed the ubuntu on my pc, with dual boot, in one partition made by me. After installing, i had a problem with the grub (he didn't start when i turned on the pc), and because of that, i installed the boot-repair in trial version on a live CD, and i made the repair. After this, was all good again.
But i saw, that when i turn on the pc, on the grub, there was two windows 8 boot: "Windows 8 (sda1)" and "Windows8 (sda2)". I didn't know what to choose, so e choose one, and in another day, i choose the other to see what happens. Was everything ok. But, after do that, in my ubuntu, i couldn't no longer acess the disk of the windows 8 (that had my stuff). What is the problem? What have i done? What can i do? Please help me, it's urgent!!!!!!!

[IMG]http://i39.tinypic.com/10z0iz9.png[/IMG]
[IMG]http://i41.tinypic.com/2199lxz.png[/IMG]

---

### Post by Elfy on 2013-08-31
*Thread moved to **Absolute Beginners Section**.*

---

### Post by oldfred on 2013-08-31
Welcome to the forums.

Please attach screen shots, not post in line. Some users do not have high speed Internet and it makes thread slow loading.

Did you turn fast boot off in Windows 8. System mentions the hibernation which is the fast boot. Windows 8 uses hibernation to make it seem like to boots faster when it really is just always using hibernation. And that often causes issues.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)
[http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx](http://blogs.msdn.com/b/b8/archive/2011/09/08/delivering-fast-boot-times-in-windows-8.aspx)

---

### Post by filipe3 on 2013-08-31
Ha, ok, sorry about that, i'm not doing it again.
But i didn't turned off the fast boot. And i don't have UEFI Bios, so, i don't have problems with the secure boot and etc.
But, after all, what have i to do, to gain acess again, on the files in ubuntu?
And, when i turn on the pc, what windows 8 i choose?

---

### Post by oldfred on 2013-08-31
Windows 8 always has fast boot whether BIOS or UEFI. With BIOS you avoid all the secure boot issues, but have the 35 year old BIOS and MBR partitions with 4 primary partition limit.

If you ran Boot-Repair it copies essential boot files from the 100MB boot partition that is normally hidden into main install and then grub2's os-prober sees boot files in both boot partition usually sda1 and main install usually sda2.

---

### Post by filipe3 on 2013-08-31
I understand, then, i have to turn of the fast boot, and it's done? After that i have to do a reset on my pc? And what boot should i inicialized?

---

### Post by oldfred on 2013-09-01
One of the links above discusses removing the hiberfile, but I think you have to get into Windows repairs.
Some have had to use Windows repair flash drive, others have repaired it some other way but have not been clear here. 

You may have to reinstall the Windows MBR to directly boot Windows as grub's boot entry usually is too quick to let you get into repairs. Then you have to reinstall grub.

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)


 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by filipe3 on 2013-09-01
This can work?

[http://www.redmondpie.com/how-to-fix-windows-8-mbr-master-boot-record/](http://www.redmondpie.com/how-to-fix-windows-8-mbr-master-boot-record/)

P.s: sorry, but i don't understand what you mean when you said: " [COLOR=#000000]You may have to reinstall the Windows MBR to directly boot Windows as grub's boot entry usually is too quick to let you get into repairs. Then you have to reinstall grub." .[/COLOR]

---

### Post by filipe3 on 2013-09-01
[http://ubuntuforums.org/showthread.php?t=1595065](http://ubuntuforums.org/showthread.php?t=1595065)

This thread says the same problem, and they say that is a "bug" of grub. But my can't be, because i can't have acess to the main files (disk C:) on my ubuntu.

---

### Post by oldfred on 2013-09-01
If you use Boot-Repair, or your Windows repairCD or flash drive you can install the Windows boot loader to the MBR. Then you will be back to directly booting Windows and can resolve the Windows issues. Grub really only chain loads to boot a working Windows and you cannot repair or do much from grub to fix Windows.

Once Windows is working then use Boot-Repair or manually procedures from a Linux repairCD or your Ubuntu live flash drive or DVD to reinstall grub to MBR and dual boot.

---

### Post by filipe3 on 2013-09-01
So, when i make the repair of the windows will fix everything, right?
But if i use grub to repair the ubuntu, won't happen the same again?

---

### Post by oldfred on 2013-09-01
As long as you turn off fast boot which is the always on hibernation it should not happen.

---

### Post by filipe3 on 2013-09-01
Ok. I will try, and then i will post here the results.

---

### Post by filipe3 on 2013-09-05
I tried what you have said. But it didn't worked :(
I've done the boot-repair on my windows, and it told me that wasn't possible to make the repair.
It writed a log file.
What can i do?
I'm sending the log file to you see.

---

### Post by oldfred on 2013-09-05
Your text file is not a text file.

But Boot-Repair only makes minor repairs to Windows. If you have Windows issues you really need a Windows repair flash drive or get into the Windows repair console.

       Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by filipe3 on 2013-10-07
It didn't worked... There was the same problem: two entries of the windows 8 (sda1 and sda2). When i used the boot repair of the ubuntu, it asked me to make extra things: unnistall the entrie of the ubuntu, and then, it told me to choose the partition where i wanted to install the entrie. What can i do?? I don't see any way to resolve this ;(

---

### Post by oldfred on 2013-10-07
Did you use  a Windows 8 repair flash drive or CD to fix Windows? 
Or at least use Boot-Repair to install a Windows boot loader to the MBR to directly boot Windows. You have to turn off auto-repair as it will want to fix Ubuntu. Then check update MBR, choose which operating system you want to fix and which MBR or choose Windows and repair MBR of sda.
You still may be able to get into Windows repair console if directly booting Windows with f8. If not you need Windows repairs.

Better help on Windows issues as we really only know Ubuntu.
 [http://www.eightforums.com/](http://www.eightforums.com/)

---

