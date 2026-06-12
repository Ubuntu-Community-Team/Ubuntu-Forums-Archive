---
title: "Having trouble setting up a dual boot- Win8.1 and Xubuntu 15.04"
date: 2015-07-20
forum: New to Ubuntu
---

### Post by evan23 on 2015-07-20
[FONT=arial][SIZE=2]Hi, I'm pretty new to Ubuntu. I've been running xubuntu for a few months, but I've been trying to set up a dual boot of Xubuntu 15.04 and Windows 8.1 with UEFI Bios. Long story short, xubuntu appears in the boot menu but not windows.

[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html) I was following this guide, though it was designed for an older version of ubuntu. Because of that, I used a different set of commands to install boot repair.

These are the commands I used instead:

sudo add-apt repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

[/SIZE][/FONT][FONT=arial]http://paste.ubuntu.com/11907675/

Here's the pastebin data from boot repair.

By all means, this should be working. I don't understand why windows is not showing up in the boot menu despite its data still being on the hard drive.

Thanks in advance for the assistance, and sorry if I am posting this in the wrong spot.[/FONT]

---

### Post by ajgreeny on 2015-07-20
Hi evan23, and welcome to the ubuntuforums.

Are you sure this is a 64bit Xubuntu system as near the bottom of your boot-info report the paragraph
> Reinstall the GRUB of sda5 into the MBR of sda
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0
suggests it may be a 32bit system, which will be very difficult if not impossible to run in dual boot with Windows in UEFI mode.

---

### Post by evan23 on 2015-07-20
It is a 64-bit version.

I'm running 64 bit hardware as well.

---

### Post by ajgreeny on 2015-07-20
It looks as if you may have installed Xubuntu in legacy BIOS mode and I imagine windows 8.1 is in UEFI mode if was pre-installed when you purchased the machine.  Unfortunately, for this query, I have not used windows for nearly 10 years, so I do not fully understand the problems of Win 8.1 and dual booting it with *ubuntu OSs.

Did you install Windows yourself as well as Xubuntu, and if so did you use legacy BIOS or UEFI mode?

Have a good read through all the info at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for a start and come back again if necessary.  You may get some clues from that which helps you figure out why this is happening.

---

### Post by toxx on 2015-07-20
When this happened to me, running update-grub fixed the problem.

 update-grub is a program used to generate the menu.lst file used by the grub bootloader.  It works by looking in  /boot  for  all  files  which start  with  "vmlinuz-"

---

### Post by oldfred on 2015-07-20
Your drive is MBR, not gpt. And you only have the standard BIOS partitions for Windows of a 100MB boot and main install.
So both Ubuntu & Windows are installed in BIOS mode.
It does look like you booted Boot-Repair in UEFI mode, but installs are all BIOS, so best to always use CSM/BIOS/Legacy mode to boot.

Windows 8 has fast boot which really is just always on hibernation. That has to be off.
Linux NTFS driver will not mount NTFS that needs chkdsk or is hibernated.
 Windows not detected by os-prober on sda2.

Normally Boot-Repair's scripts also show NTFS mount errors.

First try Daniel_Peregolise's suggestion of running grub update. With grub2 it really is grub.cfg that is menu. Old grub legacy was menu.lst.
sudo update-grub

      
 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

With UEFI hardware you can install in either UEFI or CSM/BIOS boot mode. But once you install one system in one mode you must be consistent and always boot in that mode. You have BIOS so always boot in BIOS mode.

---

### Post by evan23 on 2015-07-21
Sudo update-grub solved the issue, thanks guys

---

### Post by ajgreeny on 2015-07-22
Great!
Please use the Thread Tools menu at the top to mark this as SOLVED.

As often happens in these situations, the simple answer works best.

Oldfred is the current dual boot expert as far as the boot-info reports are concerned, and he can read them better than anyone else I know.

---

