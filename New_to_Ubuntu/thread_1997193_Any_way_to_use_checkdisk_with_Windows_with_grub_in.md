---
title: "Any way to use checkdisk with Windows with grub installed?"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by Drjim on 2012-06-04
I have a dual boot system with ubuntu 12.04 (grub) and windows 7 on the same laptop. I have a couple of sectors in windows with deeply corrupted files according to my computer guy. He says this could be corrected with the standard ckdsk program but, with grub installed for booting ubuntu, checkdisk won't work. 

Does anyone know of a way around this? Alternately, is there any way to uninstall grub and ubuntu for now short of reformatting the hard disk?

The only alternative I was given was to reinstall windows which will wipe out at least the windows programs, some of which (practice management) had to be professionally installed. 


Thanks,

Jim

---

### Post by jtarin on 2012-06-04
Restore your Win7 MBR with method of your choosing. Do your work in Win then you can use a Live CD to reinstall Grub.

---

### Post by wilee-nilee on 2012-06-04
> **Drjim said:**
> I have a dual boot system with ubuntu 12.04 (grub) and windows 7 on the same laptop. I have a couple of sectors in windows with deeply corrupted files according to my computer guy. He says this could be corrected with the standard ckdsk program but, with grub installed for booting ubuntu, checkdisk won't work. 

Does anyone know of a way around this? Alternately, is there any way to uninstall grub and ubuntu for now short of reformatting the hard disk?

The only alternative I was given was to reinstall windows which will wipe out at least the windows programs, some of which (practice management) had to be professionally installed. 


Thanks,

Jim

Do you have a recovery or install disc, grub is not your obstacle for a chkdsk. Here is a link on getting to the recovery terminal to restore the mbr if you wanted, or to initiate a chkdsk

                                  [FONT=Verdana, sans-serif][SIZE=1]http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html[/SIZE][/FONT]
  

If no disc you can try a f8 as soon as you boot windows and see if the safe boot with a command prompt is available.

We basically need to know your tool kit here.

---

### Post by oldfred on 2012-06-05
I used a Windows 7 repair USB to run chkdsk on my XP NTFS partition and it worked a bit better than the XP version. You should have a repair CD or USB anyway, just in case.


Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Drjim on 2012-06-08
> **jtarin said:**
> Restore your Win7 MBR with method of your choosing. Do your work in Win then you can use a Live CD to reinstall Grub.


Thanks for replying. I've gotten several good suggestions that all seem to agree! I'll give it a try and let you know how I do.


Thanks again,

Jim

---

