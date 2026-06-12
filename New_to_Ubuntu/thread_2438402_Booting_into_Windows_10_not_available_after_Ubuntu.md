---
title: "Booting into Windows 10 not available after Ubuntu 18.04 installation"
date: 2020-03-11
forum: New to Ubuntu
---

### Post by mastia on 2020-03-11
Hello there,

I am new to Linux and just installed Ubuntu on my laptop. I also have Windows 10 on here but I am unable to boot into it.

On boot, the grub list does not show and Ubuntu boots immediately.

I have run the following command to update grub but still no luck.

>>sudo update-grub2


I also ran boot repair and have the following output URL that could be of help getting advice from you guys.

[https://paste.ubuntu.com/p/nVdfJ7fs8x/](https://paste.ubuntu.com/p/nVdfJ7fs8x/)

Please let me know what I am missing and if there is anything else in terms of information I can offer.

Thanks in advance.

---

### Post by Impavidus on 2020-03-11
It appears that your hard drive uses mbr partitioning. This is old-fashioned and uncommon for Windows 10, but may happen if this Windows was upgraded from Windows 7 or before or if Windows wasn't pre-installed. Wth mbr-partitioning, Windows must be installed in bios mode (i.e., old-fashioned. Nothing really wrong with that.). You Ubuntu is running in UEFI mode (i.e., modern) and the hard drive has an EFI partition as required by UEFI mode, but you also have grub installed in the mbr, which is the old-fashioned method.

The grub bootloader can only boot Windows if both Windows and Ubuntu are installed in the same mode. As you cannot convert the already installed Windows to UEFI mode, you have to change your Ubuntu to bios mode. Probably best to reinstall. Configure your UEFI to legacy mode (which emulates the old-fashioned bios), then reinstall Ubuntu. The EFI partition can be deleted.

Clear?

---

### Post by mastia on 2020-03-11
Hey,

Thanks for your response.

You are spot on with your diagnosis, Windows was not pre-installed. :-)

I have 2 questions.

1. To configure my UEFI to legacy mode, I would do that during the installation of Ubuntu?
2. This would not affect my Windows installation as is?

Thanks again.

---

### Post by Impavidus on 2020-03-11
1: You have to do this before booting the live disk. It looks like the computer was on legacy mode before, but was changed to UEFI mode before installation of Ubuntu. Although the presence of grub in the MBR suggests some trial-and-error during the installation process.

2: It should make Windows bootable again.

I don't know exactly what happened to your computer. Most likely, switching to legacy mode and reinstalling Ubuntu works, but I can't be sure. Have you got backups of all your important files? It's easy to loose them.

---

### Post by oldfred on 2020-03-11
How you boot install media is then how it installs, so you have to boot installer in BIOS/Legacy/CSM boot mode.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

You can repair system, by moving boot flag back to sda1 and booting Windows.
Make sure Windows fast start up or hibernation is off.
Then using Boot-Repair's Advanced mode, booted in BIOS mode, choose the full reinstall of grub. That will uninstall the grub UEFI version and install the grub BIOS boot version.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

But since newer UEFI hardware, you may want to consider a reinstall of Windows in UEFI boot mode.
Microsoft has required vendors to install Windows in UEFI boot mode since Windows 8 released in 2012. It allows users to install in BIOS boot mode mostly for compatibility with Windows 7 upgrades or older hardware.

Ubuntu lets you install in UEFI boot mode to MBR partitioned drives, but probably should not. When Windows is in BIOS boot mode on MBR partition boot flag must be on the NTFS primary partition with Windows boot files. And UEFI requires boot flag on the ESP - efi system partition. And you cannot have two boot flags, so cannot have UEFI & Windows BIOS boot on same drive.

Grub only boots working Windows. Better to have UEFI as then you can dual boot and when Windows needs repairs you can directly boot it. 

With BIOS and only one MBR, you have to temporarily restore Windows boot loader to MBR, fix Windows and then restore grub. And you really need a Windows flash drive with the Windows repair console and Ubuntu live installer and know how to add Boot-Repair or manually install grub using Ubuntu. Easier with UEFI.

---

### Post by mastia on 2020-03-11
I'll make a backup before kicking off this endeavor.

Thanks a lot.

---

### Post by mastia on 2020-03-11
Thanks for thins information.

---

