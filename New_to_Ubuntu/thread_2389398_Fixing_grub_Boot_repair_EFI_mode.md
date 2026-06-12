---
title: "Fixing grub Boot repair EFI mode"
date: 2018-04-16
forum: New to Ubuntu
---

### Post by Kusho on 2018-04-16
Okay I have Ubuntu 17.10 and Windows 10 on my system.  But when I boot there is no grub.  I installed Windows 10 first then installed Ubuntu 17.10.  To switch between them now I have to change the boot order of my bios.  I would like GRUB to pop up when I boot and give me the option of which os to boot.  Thru searching on the internet it said the best way to do this was run boot-repair from the live cd.  I tried that but it came back with the error  "The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will enable this feature. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode." So I downloaded Boot-Repair Disk iso and burned it to a dvd.  When I booted that dvd and ran boot repair again I got the same EFI error.  Thoughts?  Suggestions?

---

### Post by oldfred on 2018-04-16
UEFI and Legacy/BIOS/CSM are not compatible. 
For grub to be able to boot Windows you must have Ubuntu installed in same boot mode, both UEFI or both BIOS boot.
You also must have Windows fast start up off (Windows may turn it back on with updates).

Post link to summary report from Boot-Repair.

---

### Post by Kusho on 2018-04-16
Okay I understand some of that.  How to I tell if Windows 10 and Ubuntu are UEFI or BIOS?  I can reinstall either Windows 10 or Ubuntu or both.  I don't know how to choose between either thou when I am installing either Windows 10 or Ubuntu.  And how do I post a summery of boot-repair if it creates this EFI error as soon as it runs and does nothing?

Trying to read the link you sent but don't understand much of it.  I'll try to make sense of it.  Sorry I'm not an expert by any means.

---

### Post by yancek on 2018-04-16
You need to have your BIOS set to boot UEFI.  If you can boot Ubuntu, open your web browser and go to the Ubuntu documentation page below which explains dual booting windows/Ubuntu UEFI.  It also shows you a command you can copy to a terminal and run which will tell you if you are booting UEFI or Legacy.  If you run the command:  sudo parted -l, it will output information including telling you if you are using gpt on your disk(s) and will show if you have an EFI partition.  Also, in booting Ubuntu, you can go to the site below (second link) and use the 2nd option to get boot repair on your Ubuntu install which I understand is more current than the iso download.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Kusho on 2018-04-16
Model: ATA ST31000340AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  524MB   523MB   ntfs         Basic data partition          hidden, diag
 2      524MB   629MB   105MB   fat32        EFI system partition          boot, esp
 3      629MB   646MB   16.8MB               Microsoft reserved partition  msftres
 4      646MB   499GB   498GB   ntfs         Basic data partition          msftdata
 5      499GB   1000GB  501GB   ext4

---

### Post by oldfred on 2018-04-16
How you boot install media, UEFI or BIOS is then how it installs. That is for both Windows & Ubuntu.
UEFI boot menu should show two entries, one clearly UEFI and other just the flash drive which is then the BIOS boot.

Windows only installs to a gpt partitioned drive using UEFI. So since drive is gpt, you have Windows in UEFI boot mode. It also shows the other partitions that Windows typically has with an UEFI install.

Your sda4, ext4 partition could be your Ubuntu install, but cannot tell if UEFI or BIOS.

What brand/model system? Some require work arounds to boot Ubuntu/grub.
And you may need to run Boot-Repair, booted in UEFI mode to correctly reinstall grub in UEFI mode. It can then convert a BIOS install to UEFI (or vice-versa).

If that does not work, post link from Boot-Repair for its Summary Report, so we can see details of your install.

---

### Post by Kusho on 2018-04-17
My system is a self built system but my motherboard is ASUS ROG STRIX B350-F Gaming Motherboard, Republic of Gamers (which I think is the bios)  I have a AMD Ryzen processor.  Don't know which specific one but I can find out if you need to know.  

I don't know how to boot into UEFI mode for the Boot repair bootable cd to load and actually run so I don't know how to post it's summary report because it never generates a report

To install Windows and Ubuntu on both I booted with the specific cd in my drive and installed the os.

---

### Post by oldfred on 2018-04-17
Not sure if all the Ryzen issues are resolved.

 ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu) 
      
 Asus Prime X399-A  with AMD Ryzen 1950X  Ubuntu 16.04.3
[https://ubuntuforums.org/showthread.php?t=2380798](https://ubuntuforums.org/showthread.php?t=2380798) 
    
Another user currently trying to install
[https://ubuntuforums.org/showthread.php?t=2389240](https://ubuntuforums.org/showthread.php?t=2389240)

---

### Post by Kusho on 2018-04-17
My system is very stable in either Ubuntu 17.10 or Windows 10.  I have never had a hang.  I have loaded the nvidia drivers and have had no issues there.  I just would like to be able to boot into grub and not have to use the bios to pick which os to boot from.  I don't boot into Windows that often so having to pick from the bios is not a huge issue I would just like to be able to do it in grub.

Okay my system
 ASUS ROG STRIX B350-F GAMING AM4 AMD B350 SATA 6Gb/s USB 3.1 HDMI ATX AMD Motherboard
 AMD RYZEN 7 1700 8-Core 3.0 GHz (3.7 GHz Turbo) Socket AM4 65W YD1700BBAEBOX Desktop Processor
CORSAIR Vengeance LPX 16GB (2 x 8GB) 288-Pin DDR4 SDRAM DDR4 3200 (PC4 25600) Desktop Memory Model ...
EVGA GeForce GTX 560 1GB GDDR5 PCIe Video Card (older video card I decided to still use in this new pc build.)

---

### Post by Kusho on 2018-04-17
Okay from what [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) tells me when I boot into the Ubuntu 17.10 boot cd I am seeing the screen for the non UEFI boot and so I think my Ubuntu is a BIOS install.

---

### Post by oldfred on 2018-04-17
You do not have a working BIOS install as with BIOS boot from gpt with Ubuntu, you must have a 1 or 2MB unformatted partition with the bios_grub flag. You do not show that partition.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Kusho on 2018-04-17
Okay I figured out how to pick UEFI only in my bios but when I did that it ignored the bootable cd in the drive (first option) ignored the Ubuntu partition (second option) and booted into Windows 10 (3rd option)  The bootable cd I was trying to boot is the Boot Repair Disk Iso so shouldn't that boot in UEFI?  It won't run UNLESS I boot it into UEFI but my computer seems to ignore it when I boot in UEFI only.  I need some more thoughts.  Booting out of Windows 10 and switching back to legacy support so I can get back into Ubuntu.

---

### Post by bsodx on 2018-04-17
I'll go as much as my Ubuntu knowledge goes far, feel free to fix me though.

Can you burn the ubuntu install iso on a USB with Rufus on Windows (Don't select MBR only when formatting bootable disc)? Then shut your pc down,plug it in and get to your UEFI. There should be two options for the same disk: one says EFI boot and other says nothing but the drive. Hit the EFI, you should see a black grub screen if things go right or a purple screen with only a keyboard and accesibility icon if doesn't boot into EFI. As much as I can see this should be able to boot you in Ubuntu. You can bootrepair from there.

---

### Post by Kusho on 2018-04-17
I don't even own a usb stick so I will have to buy one of those to try that.  Shouldn't my Blu-ray burner boot in UEFI mode?  I noticed when I went into my bios to reset my system to support both UEFI and Legacy that with it in UEFI ONLY the only boot option was Windows Boot Manager.  There WAS NO OPTION TO BOOT FROM MY Blu-ray burner.  I will go buy a usb stick if that is what I have to do.  Again this is not that serious of an issue for me just would like to figure it out.

---

### Post by Kusho on 2018-04-17
Oh and if you ask this is my Blu-Ray burner
 LG Black Blu-ray Burner SATA WH16NS40

---

### Post by yancek on 2018-04-17
> Booting out of Windows 10 and switching back to legacy support so I can get back into Ubuntu.         

If you have to do that to boot, you have windows EFI and Ubuntu Legacy and until you change that, the booting process won't change.
You can re-install Ubuntu UEFI.  The Ubuntu documentation page below explains this and answers many of the other questions you asked above including Converting Ubuntu to UEFI mode.

Since you indicate you can boot Ubuntu, rather than using the boot repair iso from a CD, use the second option method explained at the boot repair site, second link below. 

[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[/URL]

---

### Post by Kusho on 2018-04-17
Yes I understand that I need to change Ubuntu into UEFI mode to fix this.  The easiest way to do that seems to be the Boot Repair Disk ISO but again I can't seem to boot in UEFI mode on my blu-ray burner.  I will buy a USB stick and try booting Ubuntu 17.10 64 ISO on there and see if I can do boot repair from there.

---

### Post by bsodx on 2018-04-17
yancek's first link indicates that you can boot form an blu-ray disk, but USB's seem to work better than CD's. I never had a problem derived form the USB. They shouldn't be that expensive.

---

### Post by oldfred on 2018-04-17
After burning many "coasters" or bad burns, I changed to flash drives. Plus when new release comes out, you can reuse it. And most now are large enough to use for data.

Some have issues with one USB port or another, some with one brand of flash drive or another, and some with the installer they use.

You can create an UEFI only bootable flash drive without an installer.
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

Boot-Repair will not fix a flash drive, it is for updating many Linux boot issues. But most often reinstall of grub or updating grub.

---

