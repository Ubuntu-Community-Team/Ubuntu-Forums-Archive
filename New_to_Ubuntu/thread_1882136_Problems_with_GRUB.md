---
title: "Problems with GRUB"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by ubchris on 2011-11-16
So, a little background:
Figured I would forever use Ubuntu. Installed 11.04 and wrote GRUB to the MBR. Ran into a freezing trackpad problem. However, my warranty doesn't cover alternative OSes. Decided [quite absentmindedly] to just wipe my hard drive from my Windows 7 retail disk. 

Well, the obvious happens: No grldr at boot, after a restart. 

I've tried to reinstall Windows completely and execute the FixMBR commands via bootrec, but nothing really happens. 

If it's really needed, I'd reinstall Ubuntu, but the obvious end result for me is reinstalling Windows solely for a couple months while my computer is in service. 

Any help? I'm at a loss :confused:

---

### Post by SheaMan on 2011-11-16
Take the box back to the warranty and tell them your nephew got a hold of it and you want it fixed. Feign total technological innocence and say something about needing to check your outlook box. They will probably roll their eyes and fixit without bothering you about the Ubuntu / OS thing :smirk:

---

### Post by ubchris on 2011-11-16
Is there any way at all that I can fix it myself, though? 

Funny how these warranties work lately; they find one foreign program [in this case Ubuntu] and they want to void my $300 warranty. 

I can follow directions, I just need the right ones. I've googled to the moon and back, and I just need to have this set. :(

---

### Post by Sealbhach on 2011-11-16
Try the [Ultimate Boot CD]("http://www.ubcd4win.com/contents.htm") to get more information on the problem. Maybe the MBR is being written to he wrong device or something.

.

---

### Post by ubchris on 2011-11-16
How do I go about doing anything with this CD? What's my next step?

---

### Post by rng on 2011-11-16
Get ultimate boot cd or ubuntu livecd or any other linux livecd. Then download boot_info_script from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) and run it as root. The output will be stored in RESULTS.txt in that folder which you can post here. It will clarify all the partitions as well as grub and booting info. That will help correcting the problem.

---

### Post by ubchris on 2011-11-16
Will do. Thanks for the help. The CD is about half done downloading, and I'll burn and run the tool. 

Thanks again.

---

### Post by David006 on 2011-11-16
Also check if the 'Wiindows Recover' CD didn't first overwrite the HDD MBR anyway.

This would destroy any chance of Linux working until you do a full re-install ..

---

### Post by oldfred on 2011-11-16
If it is just the MBR, the you can use this boot boot into Windows.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.


Then from Windows make a repairCD and from the same place run fixMBR to put the Windows boot loader in the MBR.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

