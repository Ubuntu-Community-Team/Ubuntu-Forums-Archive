---
title: "Problems after dual boot install"
date: 2015-02-25
forum: New to Ubuntu
---

### Post by danne33 on 2015-02-25
Made a dual boot install with Ubuntu 14:10 and Windows 8. After the install, it was only Ubuntu that could start and the computer couldn't find any live USB OS stick in BIOS.
But the computer could find the USB stick in Ubuntu. After making a boot repair by downloading the program boot-repair, I can now start both Ubuntu and Windows.
However the following problems do still remain:

1) The computer still can't find any live USB OS stick. But my other computers finds it in BIOS. Also tried different kind of USB sticks. Still doesn't work.
I have tried started up BIOS with Fast BIOS: "Disabled", secure boot: "Disabled", and the combination OS mode "UEFI", "UEFI + CSM" and "CSM".
In boot priority order the following options is possible: Ubuntu, Windows boot manager, SATA HDD Samsung, the rest is blank.
The computer find the USB stick in Ubuntu and Windows 8. 

2) There are several "dead" options in grub. How can I remove them?
[http://paste.ubuntu.com/10253378/](http://paste.ubuntu.com/10253378/)

3) When Ubuntu was installed. I wanted to have the last partition as a swap partition. However when I look into Gparted it seems to be an error. (See picture)
But the swap seems to be working in program gnome-disks and [http://paste.ubuntu.com/10253378/](http://paste.ubuntu.com/10253378/)
How is it with swap volume? Is it correct to say it isn't any files stored there? Is it safe to format it and install it one more time?

---

### Post by oldfred on 2015-02-25
If you installed with an encrypted /home, then swap is encrypted and gparted (and most other tools) will not see it as they should not. This in fstab says you encrypted it:
 /dev/mapper/cryptswap1


Which entries are you using to boot ubuntu & Windows. I think all the entries in 25_Custom are not required, but not sure. It used to be that Boot-Repair renamed Windows efi file and created a entry in 25_custom to boot the backed up Windows file. It does not now rename the Windows efi file bootmgfw.efi, but does rename bootx64.efi. But is bootx64.efi really grub or shim? 
Check files sizes to confirm. 

Also best to fully backup all of the efi partition before making any changes. You can just restore files if need be, not specific install like grub to MBR with old BIOS install is required.

---

### Post by danne33 on 2015-02-26
> **oldfred said:**
> If you installed with an encrypted /home, then swap is encrypted and gparted (and most other tools) will not see it as they should not. This in fstab says you encrypted it:
 /dev/mapper/cryptswap1

Problem 3 is SOLVED!

Problem 2)
> 
Which entries are you using to boot ubuntu & Windows. I think all the entries in 25_Custom are not required, but not sure. It used to be that Boot-Repair renamed Windows efi file and created a entry in 25_custom to boot the backed up Windows file. It does not now rename the Windows efi file bootmgfw.efi, but does rename bootx64.efi. But is bootx64.efi really grub or shim? 
Check files sizes to confirm. 

Also best to fully backup all of the efi partition before making any changes. You can just restore files if need be, not specific install like grub to MBR with old BIOS install is required.

```
cat 25_custom 
#!/bin/sh
exec tail -n +3 $0

menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root BCF4-1607
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI loader" {
search --fs-uuid --no-floppy --set=root BCF4-1607
chainloader (${root})/EFI/Boot/bkpbootx64.efi
}

menuentry "EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root BCF4-1607
chainloader (${root})/EFI/ubuntu/MokManager.efi
}

menuentry "efi/EFI/Boot/bkpbootx64.efi" {
search --fs-uuid --no-floppy --set=root 2555a619-0a5f-4f93-a6d4-e0eefab09bf4
chainloader (${root})/efi/EFI/Boot/bkpbootx64.efi
}

menuentry "efi/EFI/ubuntu/MokManager.efi" {
search --fs-uuid --no-floppy --set=root 2555a619-0a5f-4f93-a6d4-e0eefab09bf4
chainloader (${root})/efi/EFI/ubuntu/MokManager.efi
}


```


I have currently the following boot options:
1. Ubuntu - works and takes me to Ubuntu 
2. Advanced options for Ubuntu - works and give me several Ubuntu work options.
3. Windows UEFI bootmgfw.efi - works and takes me to Windows login screen.
4. Windows Boot UEFI loader - works and takes me to Windows login screen.
5. EFI/ubuntu/MokManager.efi - Takes me to SHIM
6. efi/EFI/Boot/bkpbootx64.efi - DEAD
7. efi/EFI/ubuntu/MokManager.efi - DEAD
8. Windows Boot Manager (on /dev/sda2) - works and takes me to Windows login screen

How can I hide the entry 3 and 4 and delete entry 6 and 7 without damaging the boot options?
Basically I want to disable complete: /etc/grub.d/25_custom 
Btw, is it safe to delete partition /dev/sda3 as it seems to be completely broken?

Problem 1) also remains...

---

### Post by oldfred on 2015-02-26
Partition sda3 is required by Windows. It also is umformated so will not show in gparted.
```
 /dev/sda3       1,638,400     1,900,543       262,144 Microsoft Reserved Partition (Windows)


```        Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

You can delete 25_custom, but I might test first. When you do a grub-update it runs all the executeable scripts in /etc/grub.d that start with two numbers & an underscore. So you can rename it or just turn off execute bit. If you want it back then just turn bit back on.


 or turn off executeable bit
sudo chmod a-x /etc/grub.d/25_custom
sudo update-grub

---

### Post by danne33 on 2015-02-26
> **oldfred said:**
> 
 or turn off executeable bit
sudo chmod a-x /etc/grub.d/25_custom
sudo update-grub

Problem 2) SOLVED!
Now is problem 2 and 3 SOLVED and just problem 1 remain.
I can't understand why BIOS doesn't show the USB stick or any other USB live stick...
I installed Ubuntu with a USB live stick and even that one doesn't work.

---

### Post by oldfred on 2015-02-26
My laptop always showed USB flash drives separately, but desktop always showed them under harddrives. But only if configured as bootable devices first.

---

### Post by danne33 on 2015-02-26
> **oldfred said:**
> My laptop always showed USB flash drives separately, but desktop always showed them under harddrives. But only if configured as bootable devices first.

Looked in gparted and their it is written "boot"-label. I was thinking to maybe reinstall (update) BIOS firmware but I never done that under Linux. 
Do you know how to do it?

---

### Post by oldfred on 2015-02-26
My motherboards had 3 ways to update BIOS.
Windows, bootable "DOS" flash drive, or a file on a FAT32 formatted flash drive. 
I always just copied file to flash drive.

Boot Flag does not determine in BIOS if drive is bootable. It is used by Windows & Syslinux from MBR to tell which partition has more boot code/files. With BIOS (not UEFI), you need the boot loader in the MBR. There is at least one brand of motherboards (Intel) that will not even let you boot without a boot flag as it checks first. Grub does not use boot flag and most systems boot without it. But we still suggest a boot flag as we do not know what system you have.

Flash drives normally need/have a boot flag as they use syslinux or Windows boot loaders and only have one partition with more boot code.

---

### Post by danne33 on 2015-02-26
> **oldfred said:**
> My motherboards had 3 ways to update BIOS.
Windows, bootable "DOS" flash drive, or a file on a FAT32 formatted flash drive. 
I always just copied file to flash drive.

Didn't fully follow you on this one. Remember that I am a n00b. There is a program in Samsung computers that is called SW update that updates all the hard drivers.
So I think I got the latest BIOS version but not sure... USB live sticks was done by the programs Unetbootin and Universal pen drive in both Linux and Windows. Didn't work...

---

### Post by oldfred on 2015-02-26
Drivers updates from a vendor will not work. They are just for Windows.
But you may have a BIOS update and most vendors then also have with the BIOS update instructions and/or downloadable boot files for creating a DOS type boot device. A few only update from Windows.

Did any grub updates accidentally get written to flash drive? That can corrupt it. But some systems also have settings in BIOS that you have to change to allow booting from flash drive. If you reset BIOS then it goes back to defaults and you have to turn on allowing boot from flash drive. Also any update to BIOS will also reset to defaults. I had to take photos of all my screens so I knew I had reset everything. Newer UEFI system reports all changes when you save, so I just wrote those down.

---

### Post by danne33 on 2015-02-27
> **oldfred said:**
> Drivers updates from a vendor will not work. They are just for Windows.
But you may have a BIOS update and most vendors then also have with the BIOS update instructions and/or downloadable boot files for creating a DOS type boot device. A few only update from Windows.

Did any grub updates accidentally get written to flash drive? That can corrupt it. But some systems also have settings in BIOS that you have to change to allow booting from flash drive. If you reset BIOS then it goes back to defaults and you have to turn on allowing boot from flash drive. Also any update to BIOS will also reset to defaults. I had to take photos of all my screens so I knew I had reset everything. Newer UEFI system reports all changes when you save, so I just wrote those down.

I have the exact same idea! But I have never installed BIOS update under a Linux computer. I am sitting on a Samsung Series 5 Ultrabook NP530U3C laptop so it is hard to reset BIOS by pulling out the battery. Do you have any idea where I can find the things you mentioned? I never done this before so I don't know what to search for and look for. Talked to Samsung support and they only say that I should reinstall the computer with Windows 8....

---

### Post by oldfred on 2015-02-27
They do show manual.
But it looks like virtually everything requires Windows, but most of it is just for Windows.
[http://www.samsung.com/us/support/owners/product/NP530U3C-A03US](http://www.samsung.com/us/support/owners/product/NP530U3C-A03US)

---

### Post by danne33 on 2015-02-28
> **oldfred said:**
> They do show manual.
But it looks like virtually everything requires Windows, but most of it is just for Windows.
[http://www.samsung.com/us/support/owners/product/NP530U3C-A03US](http://www.samsung.com/us/support/owners/product/NP530U3C-A03US)

I was in that website couple days ago but I couldn't find any firmware for BIOS.
Also I have NP530U3C-A0HSE, Does that make a difference?

---

### Post by oldfred on 2015-02-28
All the other vendors have had specific entries for a UEFI or BIOS update and then instructions on way(s) to do it.
The Samsung version I looked at only seemed to be Windows drivers. Not sure if then they do not have BIOS updates or some other method to update.
You should make sure you use your exact model if downloading BIOS. But often vendors may have same BIOS for very similar models.

---

### Post by danne33 on 2015-03-01
Now I am in deep ****. Ubuntu is broken and won't start. The only thing that starts is Windows 8. I need a way to reinstall Ubuntu. As my live USB stick doesn't work must I install it from Windows 8.

---

### Post by oldfred on 2015-03-01
Turn off secure boot in UEFI. Check if you have specific settings to allow booting from external devices.
I do not think you can install from Windows.

---

### Post by danne33 on 2015-03-02
> **oldfred said:**
> Turn off secure boot in UEFI. Check if you have specific settings to allow booting from external devices.
I do not think you can install from Windows.

It is the same as before: "The computer still can't find any live USB OS stick. But my other  computers finds it in BIOS. Also tried different kind of USB sticks.  Still doesn't work.
I have tried started up BIOS with Fast BIOS: "Disabled", **secure boot:  "Disabled"**, and the combination OS mode "UEFI", "UEFI + CSM" and "CSM".
In boot priority order the following options is possible: Ubuntu, Windows boot manager, SATA HDD Samsung, the rest is blank.
The computer find the USB stick in Ubuntu and Windows 8.

Hmm... Is there a way to install Ubuntu from virutalbox in Windows 8? 
(I don't want to have a virutal partition inside Windows. I want to have a dual boot, just as before)

---

### Post by danne33 on 2015-03-02
One step closer! I reset BIOS by pulling out the battery. Didn't work. However I manged to boot Ubuntu in command line from the advanced boot option menu. It seems that the system files are broken from an update. 
I can mount USB sticks in command line. Do you know how to start Ubuntu installation from USB stick in command line?

---

### Post by oldfred on 2015-03-02
Are you sure then USB flash drive is correct?
UEFI or BIOS only show bootable devices, so if not correctly configured it may show as a data drive but still not be bootable.
You cannot boot from Ubuntu terminal command line, you may be able to boot from grub command line if booting in the same mode UEFI or BIOS that you booted into grub with.

---

### Post by danne33 on 2015-03-02
> **oldfred said:**
> Are you sure then USB flash drive is correct?
UEFI or BIOS only show bootable devices, so if not correctly configured it may show as a data drive but still not be bootable.
You cannot boot from Ubuntu terminal command line, you may be able to boot from grub command line if booting in the same mode UEFI or BIOS that you booted into grub with.

BIOS still doesn't show USB stick or external hard drives. 
The only thing that works is Windows 8 and start Ubuntu from one of the recovery images.
Internet connection doesn't work and many of the system files are corrupt from a bad source in /etc/apt/source.list
This project seems hopeless now and was hopeless even before the system files got corrupt. 
I think I just dump the computer and buy a new one. Thanks for all the help! Learned a lot from this!

---

