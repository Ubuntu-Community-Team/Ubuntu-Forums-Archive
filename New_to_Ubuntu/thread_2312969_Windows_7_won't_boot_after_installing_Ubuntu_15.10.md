---
title: "Windows 7 won't boot after installing Ubuntu 15.10"
date: 2016-02-08
forum: New to Ubuntu
---

### Post by Robert_Bato on 2016-02-08
Hello all I am new to Ubuntu 15.10. When selecting my Windows7 partition after booting up, it shows a line in the upper left then black screen.  I've tried running boot-repair but even then the same thing happens. Can someone point me in the right direction as to how to fix this?

Here's my pastebin:  [http://paste.ubuntu.com/14997557/](http://paste.ubuntu.com/14997557/)

---

### Post by VChief on 2016-02-08
Is this for both entries of Windows or only one of them?

Does Ubuntu boot up okay?

---

### Post by Robert_Bato on 2016-02-08
Ubuntu loads perfectly fine. IIRC sda/1 is my actual windows sda/2 is a recovery partition.

---

### Post by westie457 on 2016-02-08
```
[COLOR=#000000]Device     Boot      Start        End    Sectors   Size Id Type
[/COLOR]/dev/sda1             2048 1289991073 1289989026 615.1G  7 HPFS/NTFS/exFAT
/dev/sda2  *    1436473344 1465145343   28672000  13.7G  7 HPFS/NTFS/exFAT
```

You have dev/sda2 flagged as the boot-partition. Ideally in your situation it should be /dev/sda1.

Fire up Gparted and using the right-click menus set /dev/sda1 with the 'boot' flag, remove the flag from /dev/sda2 and set it as hidden and diag.
Click the green tick at the top of the window agreeing to all of the prompts. Reboot the computer.

Let us know what happens.

---

### Post by oldfred on 2016-02-08
Boot-Repair does not fix most Windows issues. It can install a Windows type boot loader that looks for the boot flag to know what partition to boot Windows.
Grub2's os-prober does not use boot flag, but looks for bootmgr & /Boot/BCD which you have in both sda1 & sda2.

You may need a Windows repairCD or flash drive.
Or you may have to temporarily restore a Windows boot loader and see if you can directly boot Windows or use f8 to get into internal repair console.
Use Boot-Repair's advance settings and choose Windows & MBR to put a Windows boot loader into MBR. Boot-Flag must be on sda1. When Windows is fixed, use Boot-Repair to install grub2's boot loader to MBR.

Grub only boots working Windows, so you often need a Windows repair disk or the install disk to get into repair console.
       f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)


 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)

---

### Post by Robert_Bato on 2016-02-08
Thanks! I did what westie457 said and I got into a Windows startup repair which allowed me to finally boot into Windows. Solved.

---

