---
title: "Ubuntu Boot Options"
date: 2019-12-12
forum: New to Ubuntu
---

### Post by ivatt1815 on 2019-12-12
Hi, I am a complete novice as far as Ubuntu(Linux) is concerned.

I have previously been using Windows to run my flight simulator (x-plane 11). My setup is quite basic: 

Acer Veriton M2610
[COLOR=#000000]Inte(R) Core(TM) i3-2130 CPU @ 3.40Ghz[/COLOR]
[COLOR=#000000]Multi-core (2 total)[/COLOR]
Windows 7 Professional Media Center Edition
EVGA Nvidia Geforce GTX750 1GB 128-Bit GDDR5 PCI GPU
8GB DDR in 2 banks
500GB SATA hdd
Hanns-G HA191 Monitor

and I therefore have to used low settings on x-plane to get a reasonable performance. In particular the loading time is slow unless I use Xorganizer.

I have read several posts suggesting the Linux is more efficent for running x-plane, and also an SSD, so thought I would give it a try.

I purchased a a refurbished 1TB SSD and have installed Ubuntu and to my surprise Windows 10 is installed.

After installing Ubuntu I now have a dual boot option for Ubuntu or Windows 10.

I was wondering if there is a way to set Ubuntu up so that it includes my Windows 7 install, which is on a separate drive, as another boot option rather than having to keep hitting F12 to gain access to the system boot options. I should mention my W7 drive also includes a Macrium Reflect boot option (I use Macrium Reflect to make security copis of my OS drive in case of emergencies.

Thanks in advance.

---

### Post by yancek on 2019-12-12
I'm not sure I understand what happened here.  Are you saying you purchased a used drive and unknown to you, it had a version of windows 10 installed?  Seems pretty bizarre to me.  Or is this a Windows Sub-system for Linux?

You could try booting Ubuntu and running:  sudo update-grub to add windows 7 to the boot menu.  I doubt this will work because windows 10 is generally UEFI on a GPT disk so if you are booting both from the Ubuntu Grub menu, Ubuntu is probably UEFI also.  I don't think an EFI install of Grub will boot a Legacy windows 7.

---

### Post by CatKiller on 2019-12-12
> **ivatt1815 said:**
> I was wondering if there is a way to set Ubuntu up so that it includes my Windows 7 install, which is on a separate drive, as another boot option rather than having to keep hitting F12 to gain access to the system boot options.

The thing that you'll want to look for is chain-loading; Grub loads the Windows bootloader in the MBR of your Windows 7 drive and then that bootloader loads Windows 7.

I've never done it, so I can't offer more specific help than the fact it exists.

---

### Post by oldfred on 2019-12-12
Most Windows 7 installs were BIOS on MBR partitioned drives. 
Most Intel i-series chips were in newer motherboards with UEFI and CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off. 

If your new drive is BIOS/MBR then you may only need to run this:
sudo update-grub.

If some installs are UEFI and some BIOS, you can only boot from UEFI/BIOS boot menu. Once you start booting in one mode, you cannot switch. Or grub can only boot other installs in same UEFI or BIOS boot mode.

 Some UEFI boot managers use UEFI one time boot option to make it seem like you can boot both UEFI & BIOS, but you really are totally rebooting system to switch boot modes.

Since Windows only installs to MBR(msdos) drives with BIOS and Windows only installs to gpt partitioned drives with UEFI, this will show how Windows is installed. But Ubuntu lets you install in UEFI mode to MBR drives(it really should not). Post this to see partitioning.

sudo parted -l

---

### Post by ivatt1815 on 2019-12-14
Hi thanks for the replies

[B]YANCEK

[/B]You are ccorrect, when I installed the new SSD I found it had W10 Pro installed.

As for the other replies as I said I am a complete novice as far as Ubuntu is concerned so they don't make much sense to me at the moment. I think I need to familiarise myself with Ubuntu before i can understand what I am being told.

---

### Post by yancek on 2019-12-14
If you know how to open a terminal in Ubuntu, do that and run the command below which will output information on your hard drives and their partitions.  It will not change anything but might give enough info for someone to make a suggestion.

```
sudo parted -l
```

Lower case Letter L in the command.   As indicated in earlier posts, windows 10 is generally installed in EFI mode on a GPT partition.  Ubuntu will or should install in the same mode and this will enable the Ubuntu Grub bootloader to boot both Ubuntu and chainload windows.  I don't believe it will boot a Legacy install of windows which is the default for windows 7.  Also, according to the experts at the neosmart site (link below), the same applies to the windows BCD bootloader.  7 would need to be converted to EFI first.

[https://neosmart.net/wiki/fix-uefi-boot/](https://neosmart.net/wiki/fix-uefi-boot/)

What this means is that if Ubuntu and windows 10 are both EFI and windows 7 is a Legacy install, then using the F12 key is the best you will get.  Another option I can think of off hand is to remove windows 10 and reinstall Ubuntu in Legacy mode to boot 7.

---

