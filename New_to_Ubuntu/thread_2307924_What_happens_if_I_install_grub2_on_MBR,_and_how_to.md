---
title: "What happens if I install grub2 on MBR, and how to fix that?"
date: 2015-12-29
forum: New to Ubuntu
---

### Post by ProfWoland on 2015-12-29
I've tried how to make a windows xp bootable USB and I found program called multisystem and there is warning that 'grub2 will be installed on MBR', I've found somewhere that pc will be unable to boot after that, so I need to fix that before reboot, how to do that, and what 'install grub2 on mbr' means?
P.S. pc is running lubuntu 15.04

---

### Post by sudodus on 2015-12-29
Windows does not boot from USB. The Windows installer can boot from USB, but not Windows itself, except

1. Windows PE, preinstallation environment, which can be used to repair a Windows system.

2. via a virtual machine for example VirtualBox. In this case you can have an Ubuntu host system and a Windows guest system running from USB.

-o-

Multisystem is a tool to make a USB drive that can boot several linux systems running 'live' or running as installers. Maybe the Windows installer can also run from Multisystem.

-o-

If is possible to boot a PC from a drive, internal or external, it can also boot from grub2. Multisystem might use grub2, but I am not sure, it might use legacy grub or some other method. But I know that computers boot via grub2, because I have done it hundreds of times, both with installed systems, and 'grub-n-iso' systems. See these links

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Booting USB drives with grub2 and iso files 'grub-n-iso'](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_USB_drives_with_grub2_and_iso_files_.27grub-n-iso.27)

---

### Post by ProfWoland on 2015-12-29
I'm afraid that we didn't understand each other, I don't need to make win xp live usb that is not possible is far I know, I need to make bootable win xp usb drive to install win on other pc. And (according to multisystem grub2 will be installed on mbr) so, you say that I won't have any problems booting lubuntu on my pc after that, because i've found that I will be unable to boot lubuntu on my pc after that..? If means anything this is an weeery old pc, I can freely say that is from stone age :)

---

### Post by grahammechanical on 2015-12-29
I have a machine with a BIOS boot system and every time I install Ubuntu I install Grub2 to the MBR of the hard drive I am installing Ubuntu on. It works. 

You are being warned that installing Grub2 to the MBR will overwrite any existing boot loader. So, you will lose the Windows boot loader if it exists.

MBR = Master Boot Record. It is the place where the BIOS directs the motherboard to look for a boot loader. Newer motherboards have the UEFI boot system which uses the GUID Partition table (GPT) but we still speak of installing Grub2 into the MBR of the hard disk. It might not be accurate any more. I do not know for sure.

[https://en.wikipedia.org/wiki/Master_boot_record](https://en.wikipedia.org/wiki/Master_boot_record)

If the warning is about installing Grub2 to the MBR of the USB memory stick then that should not affect any boot loader on the hard disk.

Grub2 will detect not only Linux operating systems but also Windows OSes. But the Windows boot loader does not believe in the existence of any OS other than a Microsoft OS.

Regards.

---

### Post by yancek on 2015-12-29
So you are using Ubuntu to create a usb to put the xp installer on to install xp to another drive?  If it tells you Grub will be installed to the MBR to boot the windows installer it should also tell you which drive Grub will be installed to.  Each drive has a master boot record so make sure you get the correct drive.  There is not way anyone here can tell you which that is, not enough info.

The rest of the computer world would appreciate it if you did not use the internet with that outdated and unsupported operating system.  Good luck.

---

### Post by sudodus on 2015-12-30
> **ProfWoland said:**
> I'm afraid that we didn't understand each other, I don't need to make win xp live usb that is not possible is far I know, I need to make bootable win xp usb drive to install win on other pc. And (according to multisystem grub2 will be installed on mbr) so, you say that I won't have any problems booting lubuntu on my pc after that, because i've found that I will be unable to boot lubuntu on my pc after that..? If means anything this is an weeery old pc, I can freely say that is from stone age :)

I agree with the other posts trying to explain what happens with grub2, what to do and what to avoid. Please be aware, that there are no security updates for Windows XP, so it can be attacked by intruders via the internet.

-o-

Lubuntu is booted via grub2, which is normally installed into the same internal drive as where Lubuntu itself is installed.

Multisystem might use grub2 too, in this case installed into the external drive (usually a USB pendrive).

-o-

During the installation of Windows, it will overwrite the bootloader (grub2 or whatever was used) with its own bootloader. So in order to make a dual boot system, and install Windows after linux, you have to 1) re-install grub2 and 2) run 'sudo update-grub' in order to boot both operating systems.

If you install Windows first and linux afterwards, there will be a grub2 system, which will 'see' both operating systems and you have a dual boot system.

-o-

If you have a working DVD drive, it might be better to ***burn a boot DVD disk*** with the Windows XP installer and boot the very old computer from it. It is certainly possible to make a USB boot drive, with the Windows XP installer too, and it will work with most computers that are 12 years old or newer.

But really old computers might not boot from USB at all, or you might be able to ***chainload*** via ***Plop*** in a floppy disk, CD disk or DVD disk to the USB drive.

---

### Post by ProfWoland on 2015-12-30
> **sudodus said:**
> 
-o-

During the installation of Windows, it will overwrite the bootloader (grub2 or whatever was used) with its own bootloader. So in order to make a dual boot system, and install Windows after linux, you have to 1) re-install grub2 and 2) run 'sudo update-grub' in order to boot both operating systems.

If you install Windows first and linux afterwards, there will be a grub2 system, which will 'see' both operating systems and you have a dual boot system.

-o-



Thanks! This is what I want to know.

---

