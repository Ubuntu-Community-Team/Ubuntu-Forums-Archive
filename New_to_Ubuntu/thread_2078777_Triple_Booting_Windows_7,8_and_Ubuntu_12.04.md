---
title: "Triple Booting Windows 7,8 and Ubuntu 12.04"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by Sly14Cat on 2012-10-31
Hello,
About 2 months ago I decided to dual boot with Windows 7 and Ubuntu 12.04. I have it set so it boots into windows then if I choose Ubuntu it goes into grub and I choose there but if I boot into Windows it just boots Windows. I just shrunk the Windows 7 partition from 800gb to 700gb. Now I'd like to triple boot with the Windows 8 90 Day Trial I burned to a disk. Would I just stick in the disk, install the OS to the empty 100gb and all 3 OS's will be recognized by both bootloaders?

Thank You,
Sly14Cat

---

### Post by Sly14Cat on 2012-10-31
Hello,
About 2 months ago I decided to dual boot with Windows 7 and Ubuntu 12.04. I have it set so it boots into windows then if I choose Ubuntu it goes into grub and I choose there but if I boot into Windows it just boots Windows. I just shrunk the Windows 7 partition from 800gb to 700gb. Now I'd like to triple boot with the Windows 8 90 Day Trial I burned to a disk. Would I just stick in the disk, install the OS to the empty 100gb and all 3 OS's will be recognized by both bootloaders?

Thank You,
Sly14Cat

---

### Post by mahdiolfat on 2012-10-31
What's the first boot loader that comes up when your computer is first starting up? Window's boot loader or grub?

If grub is the one that comes up and lets you choose between win7 and ubuntu, then, yes, you would just install win8, and add the device to grub:

```

sudo grub-install /dev/XXX
```where XXX is where you've installed win8 (e.g. sdb1 --> windows).

You may determine XXX by:

```

sudo fdisk -l
```CAUTION: when you install win8, depending on how you have it set up, you might be UNABLE to boot into Ubuntu (that's why it's recommended Ubuntu be installed last in dual/triple boots). If this happens, hold Left Shift while booting, this should let you choose what OS to boot into.

-
Mahdi

---

### Post by oldfred on 2012-10-31
Windows installs to a primary NTFS partition with the boot flag. But second installs of Windows literally do not have any boot files and put their boot files in the partition with the boot flag. Windows then updates boot files to newest version in old boot partition and updates BCD to boot both. Grub2's os-prober then only finds one Windows install to boot, then from Windows you can boot either version.

This is now older, but it still works the same way, unless you have the new UEFI install, not BIOS install.

To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by oldfred on 2012-10-31
Threads merged. Please do not create duplicate threads as we all are volunteers and do not want to duplicate effort or confuse the issue in a different thread.

---

### Post by Sly14Cat on 2012-11-01
So when I tried installing Windows 8 I got a error that I expected. It says that I have too many primary partitions. On my disk there's a OEM Partition, A Recovery Partition, Windows 7 and Ubuntu 12.04. I've heard that I can delete the OEM Partition because Dell just uses it for its own software but I'm not sure. How about the Recovery Partition? Do I need that when I already have a recovery cd?

Thank You

---

### Post by oldfred on 2012-11-01
If you have a recovery CD, all that does is launch the boot process to use the recovery partition. A full recovery is a set of DVDs. The only reason you might want this is if you ever sell computer and buyer wants Windows without your data.
There also is a Windows repairCD. Windows confuses things a bit as its repair is also called recovery.

So make the set of DVDs and then you can delete the recovery partition. But to use that it totally reformats drive and erases everything or has to have the  original NTFS partition to reinstall to, varies by vendor. 

Best to just make a full backup of your Windows as you may have housecleaned,  updated and shrunk it.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

