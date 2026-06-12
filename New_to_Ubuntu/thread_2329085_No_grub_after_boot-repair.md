---
title: "No grub after boot-repair"
date: 2016-06-27
forum: New to Ubuntu
---

### Post by pasha8 on 2016-06-27
Hi community,

I know variants of this question have been asked many times before, but instead of making some mistaking and having to do a clean reinstall (again), I am asking for assistance here. 
After installing Ubuntu 16.04 in dual boot with windows, I ran boot-repair and the following pastebin was created: 
[http://paste2.org/9aj0YLVn]("http://paste2.org/9aj0YLVn")
Thanks in advance!

---

### Post by grahammechanical on 2016-06-27
And the problem? I am just curious. It is nice to know what the actual problem is.


> The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting), or mount the volumeread-only with the 'ro' mount option.



That could be the cause of the problem. 

> 
To install Ubuntu in UEFI mode: 


[LIST]
[*]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").) 


[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 


[*]You might want to use an [EFI-only image]("https://help.ubuntu.com/community/Installation/FromUSBStick#Creating_an_EFI-only_image") to avoid troubles with mistakenly booting the image and installing Ubuntu in BIOS mode.    


[*]Use  a supported version of Ubuntu. Support for UEFI appeared in 11.10, but  has become more reliable in next versions. Support for UEFI [SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2. 


[*]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in UEFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below) 

[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Ubuntu has been installed in EFI mode the same as Windows has been installed in EFI mode. That is correct action. But Windows is still in Fast Startup which is actually hibernation. 

Regards

---

### Post by oldfred on 2016-06-27
In addition to Windows fast start up, HP is not particularly UEFI dual boot friendly.
Most copy shimx64.efi to /EFI/Boot/bootx64.efi and boot a UEFI: hard drive entry.
the bootx64.efi is a fallback or hard drive boot entry and is the same file name (different files) used to boot a Windows installer or Ubuntu's installer.

       HP Check if Customized UEFI settings available like this  HP ProBook 4340
[http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file](http://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file)
HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]
[/URL] You can run Boot-Repair's advanced mode:
Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options. 

But that may not add an UEFI entry into NVRAM for booting hard drive.

Also HP has its system maintenance .efi files in the ESP - efi system partition. Many other vendors have to files in hidden ESP or another efi type partition. But then Boot-Repair sees all those .efi files & adds them to the grub menu.
You can delete most or all by editing 25_custom.

 # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by pasha8 on 2016-07-26
Thank you for the advice. Disabling fast start up and running boot repair with the "large ATA disk" option worked. I have about 10 entries in my GRUB panel now, but I ignore most of them and access ubuntu just fine. Thank you!

---

