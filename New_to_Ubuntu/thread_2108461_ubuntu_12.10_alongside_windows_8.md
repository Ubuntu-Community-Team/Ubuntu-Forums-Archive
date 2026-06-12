---
title: "ubuntu 12.10 alongside windows 8"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by kmelkon on 2013-01-24
OKAY, I give up!
after trying to install Ubuntu 12.10 alongside windows 8 for 3 times and ending with a problem each time, I need some help.
so I have a Dell inspiron N5010 (intel i3 - ATI GPU - 4 GB RAM - 500 GB HDD)
*I installed windows 8 on a 20 GB partition.
*then booted Ubuntu 12.10 using a live usb
*selected "something else" option
*created two partitions [one for swap area : 4 GB and one for Ubuntu root : 20 GB (ext4 - primary)]
*after installing it, I resbooted into the GRUB 2 menu and chose Ubuntu. went fine, then rebooted and chose windows 8 and it started automatic repairing which only does nothing.

So how can I do this properly, please?

---

### Post by monkeybrain2012 on 2013-01-24
Get rid of Windows. :)

Seriously, can you choose "start Windows normally" in WIn8 ? There are some Win7 machines which do that, and choosing "start Windows normally" usually works.

---

### Post by kmelkon on 2013-01-24
> **monkeybrain2012 said:**
> Get rid of Windows. :)
 
Seriously, can you choose "start Windows normally" in WIn8 ? There are some Win7 machines which do that, and choosing "start Windows normally" usually works.
 i'd love to get rid of it but I still need it for games until steam on linux has all the titles.
and I don't have that option. but thanks.

---

### Post by oldfred on 2013-01-24
I thought Windows needed more than 20GB, most suggestions have been 30GB and a lot more if installing games which can be huge.

To see details of your install, but if a Windows boot issue, you need a Windows repairCD to fix that.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

