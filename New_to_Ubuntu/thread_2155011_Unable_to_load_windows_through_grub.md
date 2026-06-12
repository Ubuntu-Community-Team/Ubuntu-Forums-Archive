---
title: "Unable to load windows through grub"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2013-06-16
Hello!

I have a computer, in which I upgraded my existing Windows to Windows 8, so I still have the BIOS, not the UEFI. When I installed Ubuntu 12.04 LTS and I rebooted, and selected the "Windows 8 (loader)" option, the computer just rebooted and returned to the same grub menu](*,). Are there any ideas on what is happening?

---

### Post by MidnightGrey on 2013-06-16
Boot-Repair is usually the first thing to try in these situations:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mark Phelps on 2013-06-16
IF you used the Ubuntu installer to shrink the Win8 OS partition, then you likely ended up corrupting the filesystem.  Boot-repair MIGHT be able to fix this -- but you should have come here first before charging ahead with the installation.  We could have told how to avoid these problems.

---

### Post by Jonathan Precise on 2013-06-17
> **Mark Phelps said:**
> IF you used the Ubuntu installer to shrink the Win8 OS partition, then you likely ended up corrupting the filesystem.

I did not use the Ubuntu installer to shrink the Windows 8 Partition. I used the GParted Live CD (the image is available [here]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.16.1-1/gparted-live-0.16.1-1-i486.iso/download")) to shrink the Windows 8 Partition. Then I rebooted back into the Windows partition to make my last backup (and to make sure that the filesystem wasn't corrupted). After that it's when I installed Ubuntu on the remaining space.

---

### Post by Jonathan Precise on 2013-06-20
> **MidnightGrey said:**
> Boot-Repair is usually the first thing to try in these situations:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I tried Boot-repair through [Linux-Secure-Remix]("http://sourceforge.net/projects/linux-secure/files/"). However, the problem wasn't fixed:(. Actually there was a new option in grub called "Windows 8 (loader) in /dev/sda2". Neither option worked to boot windows. The computer just restarted and returned to the menu.

Unfortunately, it seems that I can't paste the output log it here nor in the Ubuntu pastebin. The first reason why is that the internet connection doesn't seem to work in the Live CD (see [post]("http://ubuntuforums.org/showthread.php?t=2154753")). The second reason is that I can't save it to my Windows partition. I can't seem to access it. Any ideas of what is happening?

---

### Post by oldfred on 2013-06-20
Did you turn off fast boot as Windows is always hibernated.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by Jonathan Precise on 2013-06-20
I had Fast Boot on. However, when I wanted to mount the partition, it asked me if I wanted to remove the hyberfile, which I assume is the file where windows stores the information for Fast Boot. I removed it, and then restarted. The problem continued.

---

### Post by sandyd on 2013-06-20
I am not familiar with Windows 8 anymore, but if you have the disc, there should be a startup repair option avaliable, which will wipe the Ubuntu bootloader, and (hopefully) allow you to boot back into Windows.
From there, if Windows startup repair works and allows you to startup to windows, you can use Boot Repair to reinstall the Ubuntu bootloader (grub)

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by sandyd on 2013-06-20
> **ahallubuntu said:**
> You might be able to do what sandyd suggests but after you get Windows booted again, you can try using the Windows 8 bootloader to boot Ubuntu instead of using Grub to choose which OS to boot.  I've done it with Windows 7 but not with Windows 8, but I assume there is a way to do it.

As far as I know, [EasyBCD support windows 8]("https://neosmart.net/blog/2012/announcing-easybcd-2-2-windows-8-dual-booting-and-more/")

---

### Post by fantab on 2013-06-21
> **Jonathan Precise said:**
> I did not use the Ubuntu installer to shrink the Windows 8 Partition. I used the GParted Live CD (the image is available [here]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.16.1-1/gparted-live-0.16.1-1-i486.iso/download")) to shrink the Windows 8 Partition. Then I rebooted back into the Windows partition to make my last backup (and to make sure that the filesystem wasn't corrupted). After that it's when I installed Ubuntu on the remaining space.

Ubuntu installer also uses Gparted. It is not a good idea to 'manage' Windows partitions with Gparted. You must only use Windows Disk Management. With Gparted it MAY or MAY NOT create problems.

Disable Fast Startup un Windows8: [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Also post the output of [BootInfo Script]("http://bootinfoscript.sourceforge.net/").

---

### Post by Mark Phelps on 2013-06-21
> **Jonathan Precise said:**
> I did not use the Ubuntu installer to shrink the Windows 8 Partition. I used the GParted Live CD ...
That's what the Ubuntu installer uses.  It's generally a bad idea to use Linux utilities on Windows filesystems, especially the OS partitions of Win7 and Win8.  

I really wish Canonical would REMOVE the resizing option from the Ubuntu installer (when it detects Win7 or Win8) -- but hey, I don't have any influence on them.

You might be able to fix with Boot-Repair, but that doesn't always work.  Had you asked before you did this, I could have told you how you could have created a free Win7 Repair CD -- but you have to be able to boot into Win7 to do that.

If boot-repair fails, there is an option to PURCHASE and ISO image you can use to make a Win7 Repair CD.  

Just let us know how it goes.

---

### Post by oldfred on 2013-06-21
If you have access to another computer with the same 32 or 64 bit, but any version of Windows from work, school or a friend, you can make a repairCD or for Windows 8 a repair flash drive.

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

### Post by Jonathan Precise on 2013-06-22
Hello!

EasyBCD did fix my problem:). Thanks for the help!

---

### Post by zrdc28 on 2013-06-22
You should shrink the partician using windows 8, then use gparted to set up the particians for use with ubuntu not touching the windows partician.  If you will download a program called "super grub" it will
boot windows up for you.

---

