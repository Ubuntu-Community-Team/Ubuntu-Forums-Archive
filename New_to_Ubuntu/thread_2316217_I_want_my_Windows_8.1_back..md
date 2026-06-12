---
title: "I want my Windows 8.1 back."
date: 2016-03-06
forum: New to Ubuntu
---

### Post by Onett1984 on 2016-03-06
I've installed Ubuntu 14.04 alongside Windows 8.1 and have done some partition crap. I tried Ubuntu for a while and wanted to go back to Windows, but when I try to boot it through GRUB (that's a name for this lame purple menu,yes?), this shows up: "Windows failed to boot" and blablabla.

I googled my problem and found Boot Repair. I somehow installed it and tried recomended setting, but it says:

"The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will activate the function. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode." 

What have I made wrong? What do I need to do? My main goal is to launch Windows. Sorry for bad English. Any help is appreciated.

---

### Post by cwmoser on 2016-03-06
Sorry to hear that.  
You have not lost much - Windows 8.1 is pretty lame :-)
I know you do not want to hear that.
But, I really think you can recover the boot menu.
I've done the same thing and I used a Distro Linux that had 
a Boot Recovery menu option to put back all the OS's it can discover
on all of my hard drives.

Boot from the Ubuntu CDROM you used and see if you can find that menu option.

Carl

---

### Post by TheFu on 2016-03-06
Don't know your specific issue. Sorry.

But it reads as if one OS is installed in legacy BIOS mode and the other is installed in UEFI mode. That means that changing the BIOS setting is required to access the other OS.  I would just restore from the whole disk backup that I made prior to installing Ubuntu. That way the machine would be exactly like it was before I tried Linux at all.  Anytime any partitioning is done, having a whole disk backup is really important.

---

### Post by Onett1984 on 2016-03-06
Plugging live-USB with Ubuntu or anything does nothing. There are no other menu or extra options.

---

### Post by oldfred on 2016-03-06
If system has Windows 8 or later pre-installed, then you just go into UEFI or one time boot key like f10 or f12 and boot Windows.
You can in UEFI/BIOS change boot order to boot Windows first.

If you reinstalled Windows in BIOS mode then you have to restore a Windows boot loader. UEFI has all boot loaders in the ESP - efi system partition and UEFI stores all bootable systems in its NVRAM. It also is a boot manager with a menu similar to the grub menu you do not seem to like.

If totally removing Ubuntu from system, you need to remove /EFI/ubuntu folder from ESP. Easier from Ubuntu live installer as Windows does not show ESP. You have to mount it in Windows.
And you have to go into UEFI and remove the ubuntu entries (usually two) from NVRAM.
       Really UEFI boot menu 
[URL="http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu"]http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu

[/URL]
 Check entry is there from Ubuntu live installer.
sudo efibootmgr -v 


   Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu
[URL="http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743"]http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743
[/URL]
 [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr) 

[URL="http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743"]
[/URL] 

[URL="http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu"]
[/URL]

---

### Post by Onett1984 on 2016-03-08
I apprrciate your help but I don't need to delete Ubuntu. I just want to boot Windows. Can you give me more detailed help on this, please?

---

### Post by Onett1984 on 2016-03-08
&#12542;(&#1086;-&#969;&#65381;)&#65417;&#8978;&#9733; Okay, thanks, first solution worked for me. I entered BIOS, changed boot order to UEFI, saved and booted into Windows successfully. (&#3665;&#8226;&#768;&#12610;&#8226;&#769;)&#1608;&#10023;

---

### Post by oldfred on 2016-03-08
If you want to dual boot from grub menu, Ubuntu has to be installed in UEFI mode and Windows fast start up must be off.
Secure boot must also be off in UEFI. If you want secure boot on, then you can only boot from UEFI boot menu or one time boot key, not grub.

If Ubuntu is in BIOS mode, grub can only boot systems installed in BIOS boot mode. But you can convert to UEFI using Boot-Repair's advanced mode. It really just uninstalls grub-pc (BIOS) and installing grub-efi-amd64 (UEFI).

       Fast Startup off (always on hibernation)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

---

### Post by terry_gardener on 2016-03-09
like it has been said before in this thread. 
the situation is that windows is installed using uefi and ubuntu has been installed using legacy mode. 
if you want to get rid of ubuntu completely just repair the windows bootloader/mbr. 
[http://www.fixedbyvonnie.com/2013/12/how-to-repair-the-efi-bootloader-in-windows-8/#.VuB-HiZb_CI]("http://www.fixedbyvonnie.com/2013/12/how-to-repair-the-efi-bootloader-in-windows-8/#.VuB-HiZb_CI")

then when the bootloader is repaired you can delete the ubuntu partition and extend your windows partition from within windows. (warning do not remove the ubuntu partition before repairing windows boottloader

if you want to continue to use ubuntu and windows in dualboot together the you need to install ubuntu in uefi mode not legacy. on my computer/motherboard when you go into boot menu select usb: name of usb flash drive for (legacy mode) or uefi usb name of flash drive for uefi mode.

---

