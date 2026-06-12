---
title: "Grub doesnt regonize windows 8 OS"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by gman2015 on 2013-06-22
I screwd up on the dual boot installatoin of ubuntu 12.04 causing my partions to get all screwed up and not showing my widnows 8 partition anymore. I used testdisk to recover and fix my partition. The grub boot menu still does not regonize windows 8 after i tried to update it. I used boot-script-info and the results are attached. [ATTACH]244042[/ATTACH]

Is there anyway to get Windows 8 back?

---

### Post by oldfred on 2013-06-22
If sda2 is your Windows it is repairable, but you need a Windows repair flash drive or CD. Windows 7 or 8 normally installs to two partitions, a small 100MB boot/repair partition which has two boot files and the main partition which is the full install with one more boot file.

       Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You need a Windows 8 bootmgr and create a BCD for Windows to boot. You can add them to your sda2 partition.
You need to move boot flag from sda1 to sda2. Grub does not use a boot flag, but Windows has to have it to know which partition to boot from or repair.
Also if you changed partition size at all you will need to run chkdsk.

Do you have a Windows 8 version of a repairCD? If you know anyone with Windows 8 from work, school or a friend.
Since you have BIOS with MBR partitioning I think the process is essentially the same for 8 as 7. The UEFI version is for the new pre-installed versions of Windows 8.

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by gman2015 on 2013-06-22
I dont have a windows 8 repair tool but i can get my hands on one.

Sorry, Im new to all this but how would I go about adding the windows 8 bootmgr and creating a BCD? Is that from the repair cd? How do I move the boot flag as well?

Thanks for the quick response

---

### Post by oldfred on 2013-06-22
You can use gparted from live installer. You just click on the partition & right click to mange flags. Set boot flag.

In Windows it is the active partition. From Windows command line it would be the make active command, not sure of details.
You can just copy bootmgr as long as it is Windows 8 version. And run Windows repair to create a BCD or use editBCD.

There is also EasyBCD which some have used. The also sell the full repairCD for Windows. (it used to be free).
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

This was Windows 7, but 8 should be the same.
 oldfred's Windows Vista/Win7 repair links posts #7:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)
Make sure boot flag is set for any partition you try to repair.

More info:

 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by gman2015 on 2013-06-26
I got a windows 8 recovery disk but it has the same problem as ubuntu. It does not regonize the operating system. I havent been able to find any bootmgr files. I am not able to fix it because I do not have access to a windows command line.

---

### Post by oldfred on 2013-06-26
Did you move the boot flag to sda2? 
Windows only repairs the NTFS partition with the boot flag. Grub does not use boot flag. But Windows has to have it.

---

### Post by gman2015 on 2013-06-27
I did move the boot flag to sda2.

---

### Post by gman2015 on 2013-06-27
In gparted it says the sda2 is not mounted but the option to mount it is greyed out. Any way to get around that?

---

### Post by gman2015 on 2013-06-27
I got it to mount.

---

