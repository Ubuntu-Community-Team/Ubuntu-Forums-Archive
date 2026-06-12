---
title: "BOOTMGR is Missing - Ever since I installed Ubuntu?"
date: 2013-11-09
forum: New to Ubuntu
---

### Post by mazaru2005 on 2013-11-09
Hello,

So I installed Ubuntu - I'm sorry, I don't remember the version, but it  was 12 point something and had support until 2017... I installed it from  a file called wubi.

This happened on a different laptop, with a copy of Windows 7. As it  happens, my Operating System Crashed, and my local hardware shop  installed a non-genuine copy of Windows (despite me asking him to load  Genuine Windows.) So I installed Ubuntu, alongside Windows 7.

Now, I decided to go back to Windows 7 to try and see whether I could  uninstall it. But the directions were too complicated... I shut down the  computer. (It's possible I may have done something part-way but as far as I recall I didn't do anything) When I next booted it, I got the message "BOOTMGR is Missing"  Press Ctr+Alt+Del to restart.

I tried changing the order of the boot... no go. I checked Ubuntu  guides... one of which suggested unetbootin windows to install  boot-repair-disk-32.iso on to a USB stick, and use that to try and fix  the problem.

My question though, is that this fix seemed to be for GRUB issues  (whatever those are). Will this fix work for BOOTMGR? Is the way I'm  going about doing it fine? And/or is there a way I can install Ubuntu on  the laptop? Yes, I read the "How to install Ubuntu on a flash-drive".  What I'm wondering though, is with the BOOTMGR issue... would Ubuntu install?

I'm a complete beginner at Ubuntu... not so much of an expert in  handling computers either. I'm currently using my other laptop running  Windows 8.1, and any advice/suggestions would be appreciated. I'll check  back every ten-fifteen minutes so please tell me if I forgot to mention  something!

EDIT: Tried loading unetbootin with the repair iso from the usb. Maybe I did something wrong, it says: SYSLINUX 4.06 EDD 2012-10-23 Copyright (c) 1994-2012 H. Peter Alvin et al. Could not find kernel image: CONFILE. boot: _ (blinking cursor)

---

### Post by oldfred on 2013-11-09
There is no reason to use 32bit version, try a 64 bit version.

The error message is Windows boot loader trying to boot from a partition that is either not NTFS or is not correctly configured as NTFS. 
Boot-Repair can only fix minor Windows issues like adding a Windows type boot loader, but you need to either change boot flag or active partition to the correct Windows boot partition and/or run chkdsk from Windows or your Windows repairCD or flash drive.

Wubi is being discontinued as it does not work with the new gpt partitioning that new UEFI computers now have. All Windows 8 pre-install systems are UEFI secure boot, not the old BIOS boot with MBR(msdos) partitioning.

I do not know if you can use a Windows 8 repair flash drive on Windows 7? But I have used a Windows 7 repair flash drive on my XP to run chkdsk.
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

