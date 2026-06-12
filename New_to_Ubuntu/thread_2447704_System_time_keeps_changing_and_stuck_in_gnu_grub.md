---
title: "System time keeps changing and stuck in gnu grub"
date: 2020-07-24
forum: New to Ubuntu
---

### Post by woody83686 on 2020-07-24
System info:
Hp Pavilion TS Sleekbook 14
System board 18FC
Intel Celeron CPU 877@1.40 GHz
8 GB total memory
BIOS version F.1A
BIOS vender Insyde 
Factory installed Operating system Windows 8
Installed Ubuntu 20.04
GNU Grub version 2.04

My daughter had this computer and it had viruses. I installed Ubuntu, upgraded the memory from 4GB to 8GB, and installed a new CMOS battery while I had it apart. Ubuntu was working great for a few weeks and I was customizing it. I used it to print a document and came back to it later and it had frozen. I had to hold the power button to get it to turn off. When I opened the computer the next day it booted up fine and ran but, there was a error message that said it was missing files. I shut the computer down and the next time I turned it on it wouldn't boot. It would stop at the GNU Grub screen that says GNU Grub version 2.04 grub>. I went to the BIOS menu and I noticed the system time was wrong. I changed it and tried restarting with the same results. 
At this point I decided to reinstall Ubuntu 20.04 with my flash drive to fix it. I was able to install and then I restarted. It still stops at the GNU Grub screen. I checked the BIOS menu again and the system time was wrong again. 
I don't know what else to try. I would appreciate any advice you have.
Thanks

---

### Post by CatKiller on 2020-07-24
> **woody83686 said:**
> I used it to print a document and came back to it later and it had frozen. I had to hold the power button to get it to turn off. When I opened the computer the next day it booted up fine and ran but, there was a error message that said it was missing files. I shut the computer down and the next time I turned it on it wouldn't boot. It would stop at the GNU Grub screen that says GNU Grub version 2.04 grub>. 

This part sounds like a failing drive. You can run fsck and the SMART tests from the live USB. 

> I was able to install and then I restarted. It still stops at the GNU Grub screen.

This part sounds like a mismatch between UEFI and BIOS: installed one way and booted the other way. Or a drive that's very dead. 

All OSes other than Windows use UTC rather than local time for the hardware clock, so the time displayed there will differ from local time by however many hours your timezone is different from UTC.

---

### Post by ActionParsnip on 2020-07-24
Do you have the latest BIOS?
If you use NTP it'll keep the date and time in sync.
Did you push the CMOS battery in fully?

---

### Post by woody83686 on 2020-07-26
Thank you so much for your advice. I have used the HP utility for checking the health of the drive and it came back good. 
I am intrigued about what you said about a mismatch between UEFI and BIOS -- how do I check for that?

---

### Post by woody83686 on 2020-07-26
> **ActionParsnip said:**
> Do you have the latest BIOS?
If you use NTP it'll keep the date and time in sync.
Did you push the CMOS battery in fully?

Please forgive me for being a newbie. I have the BIOS that was on the computer from HP. Can I get an update to the BIOS if I am not using the original operating system (Windows)? 

When I get a chance I can look at my CMOS battery. I have to take the whole board out of the computer to get to it. 

Thank you for your advice.

---

### Post by CatKiller on 2020-07-26
> **woody83686 said:**
> I am intrigued about what you said about a mismatch between UEFI and BIOS -- how do I check for that?

BIOS is really, really old. UEFI is newer, but has still been around a while: every motherboard for the last decade or so has been UEFI. Because BIOS is so old, it's pretty straightforward to emulate; that setting is generally called "Legacy," "Compatibility Support Module," or "CSM." 

BIOS used MBR partitioning, and the bootloader was stored in the Master Boot Record, and then chainloaded the next part of the boot process from elsewhere on the disc. UEFI uses GPT partitioning, and all the bootloaders have one partition to store them in, called the EFI System Partition. 

Ubuntu can be booted and installed in either UEFI or BIOS mode, depending on your settings. If you boot the installer in UEFI mode, Ubuntu gets installed in UEFI mode, and vice versa. 

If you install in one mode and then try to boot in the other, though, your machine won't find the bootloader, and booting will be unsuccessful. 

> **woody83686 said:**
> Can I get an update to the BIOS if I am not using the original operating system (Windows)? 
Generally, yes. You put your downloaded file somewhere the UEFI can read from, like the ESP or a FAT-formatted thumb drive, go into your UEFI setup, and point it at the file.

---

### Post by woody83686 on 2020-08-09
> **CatKiller said:**
> BIOS is really, really old. UEFI is newer, but has still been around a while: every motherboard for the last decade or so has been UEFI. Because BIOS is so old, it's pretty straightforward to emulate; that setting is generally called "Legacy," "Compatibility Support Module," or "CSM." 

BIOS used MBR partitioning, and the bootloader was stored in the Master Boot Record, and then chainloaded the next part of the boot process from elsewhere on the disc. UEFI uses GPT partitioning, and all the bootloaders have one partition to store them in, called the EFI System Partition. 

Ubuntu can be booted and installed in either UEFI or BIOS mode, depending on your settings. If you boot the installer in UEFI mode, Ubuntu gets installed in UEFI mode, and vice versa. 

If you install in one mode and then try to boot in the other, though, your machine won't find the bootloader, and booting will be unsuccessful. 


Generally, yes. You put your downloaded file somewhere the UEFI can read from, like the ESP or a FAT-formatted thumb drive, go into your UEFI setup, and point it at the file.

I went into the Boot menu and I tried running in Legacy mode and in EUFI mode and I get the same result. I tried installing again from EUFI mode and Ubuntu installs and after the computer tells me to remove the usb flash drive it goes to the GNU grub screen and stays there. (I am sharing some pictures of the screen at the boot menu and the grub screen). If I hit control-alt-delete at the grub screen I get a message that pops up and goes away quickly saying,

System BootOrder not found. Initializing defaults. Creating Boot entry "Boot0010" with label "ubuntu" for file "\EFI\ubuntu\shimx64.efi".  

I am hoping that the pictures might help with a diagnosis. I also tried running the SMART DATA & SELF TESTS from Ubuntu after the install and everything came up ok. I am a little concerned with the number of entries in the Boot Manager menu. I am not sure if this is related to my problem. 

I am hoping that the pictures might help in a diagnosis. Thanks again for your time in helping me figure this out. 

[ATTACH=CONFIG]286660[/ATTACH][ATTACH=CONFIG]286661[/ATTACH][ATTACH=CONFIG]286662[/ATTACH]

---

### Post by dino99 on 2020-08-10
When you start booting, hold down the key for getting the recovery mode (usually F2, but can be something else with your model); then activate the network inside that menu, and open a terminal: run:

sudo blkid
then edit fstab to check that it match the uuids output given by blkid above  (sudo nano /etc/fstab , do the required change(s) if needed, then save)

also glance at 'journalctl -b' output to know about error (red lines) and warning (yellow ones, but harmless)

hopes the virus you talked about have not corrupted the bios/uefi :confused: ; otherwise install a new version to get rid of it.

---

### Post by woody83686 on 2020-12-22
I think I have found the problem but, I need some advice. I found out that if I pressed F9 to go to the boot menu and selected Boot From EFI File&#8594;partition 2&#8594; <EFI>&#8594; <BOOT>&#8594; fbx64.efi it tells me boot order not found but, it would boot and open Ubuntu. Now that I can open Ubuntu, I was able to open the Disk utility and found that there are three partitions sda1, sda2, and sda3. I am including screenshots below. As you can see, the second partition sda2 has the boot in it. I don’t think know why my partitions are set up this way….I let Ubuntu set it up when installing. I think that the boot needs to be in partition 1 (sda1). Please if you could give me some advice on how I should have my partitions set up and if some should be removed I would appreciate it. Thanks.

---

### Post by CelticWarrior on 2020-12-22
First things first, the "Disk is OK, 392 bad sectors" actually mean the disk is NOT OK. At the moment it is after a successful format that set those bad sectors asside but the situation can get worse.

I would replace it, rendering all following points moot except the battery. Regarding the issue of the system clock either the replaced battery is dead or isn't properly inserted or, worse, the problem is in the motherboard itself.

Secondly, it's definitely UEFI, not BIOS. This distinction is important for the way OSes should be installed (UEFI mode) and the recommended partitioning of the drive (GPT). It happens that you have a UEFI installation (or several attempts) in a MBR ("msdos") partitioned drive. Windows wouldn't let you do that but Ubuntu does and probably shouldn't. It is what it is and the new installer unfortunately have been doing weird s... like what you showed in the first screenshot.

Again, I would replace the drive. With a new blank drive the installer would default to GPT automatically. If keeping the current one I would first make it GPT before reinstalling. In the live session open Gparted > Device > New partition table... Chose "GPT". This will remove all previous partitions. Then proceed with the installation selecting the whole drive.

As suggested before I would also update the firmware (UEFI) if an update has been released by the manufacturer, before reinstalling.

---

### Post by rsteinmetz70112 on 2020-12-22
> **ActionParsnip said:**
> 
Did you push the CMOS battery in fully?
I once forgot to remove the plastic film on the battery contacts. :eek:

---

### Post by woody83686 on 2020-12-24
Thank you for the advice. I will look for a replacement drive and reinstall the operating system in UEFI mode.

---

