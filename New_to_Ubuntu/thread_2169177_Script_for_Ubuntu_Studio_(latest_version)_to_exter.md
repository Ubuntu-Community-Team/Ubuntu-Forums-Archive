---
title: "Script for Ubuntu Studio (latest version) to external drive with GRUB"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by ndiniz on 2013-08-20
I have Windows 8, and was wondering if there's a utility that I could use somewhere online to help me create a script that will allow me to run Ubuntu Studio from my external drive. I have no idea of where GRUB should go, so if anyone has any ideas, I'd really appreciate it. 

I found something at this link that might help me [http://forums.linuxmint.com/viewtopic.php?f=46&t=67934](http://forums.linuxmint.com/viewtopic.php?f=46&t=67934)

---

### Post by rai_shu2 on 2013-08-21
Most computers let you configure the BIOS if you're holding the Del key when it starts up. Some let you select a boot drive if you're holding F11 or some other special key.

---

### Post by ndiniz on 2013-08-21
I am actually going to give you the current setup of my BIOS and from there, someone can help me make the required changes to my BIOS before I attempt installation. It will take some time.

---

### Post by ndiniz on 2013-08-22
Almost finished writing down my current computer's BIOS configuration. I should be finished writing it all down sometime today.

---

### Post by rai_shu2 on 2013-08-22
Just the name of the BIOS should be sufficient.

---

### Post by ndiniz on 2013-08-22
OK, it is "Lenovo BIOS Setup Utility". I have a Lenovo H430.

---

### Post by rai_shu2 on 2013-08-23
Right. The manual for your computer states:

> [FONT=sans-serif]How can I start the BIOS setup utility?
[/FONT]
[FONT=sans-serif]To start the BIOS setup utility:[/FONT]
[FONT=sans-serif]1.[/FONT]
[FONT=sans-serif]Shut down the computer.[/FONT]
[FONT=sans-serif]2.[/FONT]
[FONT=sans-serif]Repeatedly press and release the F1 key after turning on the computer, then 
[/FONT]
[FONT=sans-serif]select [/FONT]
[FONT=sans-serif]Startup
[/FONT]
[FONT=monospace]&#8594;
[/FONT]
[FONT=sans-serif]Boot Priority

Aside from that, I guess you'll need to look at what you can do there.
[/FONT]

---

### Post by ndiniz on 2013-08-23
I will go into my BIOS later, and I do believe that there are other settings I have to change. I will report the settings that might need to be changed and see what needs to be done.

---

### Post by ndiniz on 2013-08-23
I figured I'd give you the current settings of my PC's BIOS & their options, because I realize parts of the BIOS have to be changed before I can run the installation. I just want to make sure everything is right before I do anything else. I don't want to go through trial & error here.

---

### Post by ndiniz on 2013-08-24
here is the current configuration:

[FONT=arial]System info:

[/FONT]
[FONT=arial]Machine Type & Model: 10091
System Serial Number: ES10403752
System UUID: CE9F2BC0-044F-11E2-905E-C02574772F00
Ethernet MAC address(onboard): ec-a8-6b-6e-48-4e
BIOS Revision Level: ESKT19A
License status: Win8 STD MM DPK IPG

[/FONT]
[FONT=arial]System Summary

[/FONT]
[FONT=arial]CPU Type: Intel(R) Core(TM) i5-3330 CPU @ 3GHz
CPU Speed: 3000Mhz
CPU Core Count: 4
Installed Memory: 8192 MB (DDR3)
Memory Bus Speed: 1600Mhz
Active Video: IGD
Onboard Ethernet & Audio Support: Enabled

[/FONT]
[FONT=arial]Devices:

[/FONT]
[FONT=arial]USB: Enabled (Option: Disabled)
SATA Mode: AHCI Mode (Option: IDE Mode/Disabled)
Onboard Ethernet Controller: Enabled (Option: Disabled)
LAN Boot Agent: Disabled (Option: Enabled)
PXE IP4&6 network stack: Enabled (Option: Disabled)
Select Active Video: Auto (Option: IGD/PEG)

[/FONT]
[FONT=arial]CPU Setup:

Intel(R) SpeedStep Tech: Enabled
Turbo Mode: Enabled
Intel Virtualization Technology: Enabled
Core Multi-Process is automatically Enabled and cannot be disabled
CPU ID: 306a9
Microcode Revision: 12

[/FONT]
[FONT=arial]Power

[/FONT]
[FONT=arial]ACPI Standby Mode: S3 (STR) (Cannot be adjusted)
After Power Loss: Power Off (Option: Power On/Last State)
ErP: Disabled (Option: Enable)[/FONT]
[FONT=arial]Image Execution Policy[/FONT]
[FONT=arial]Secure Boot Status: User Mode 
Secure Boot: Enabled (Option: Disabled)
(Note, by highlighting "Reset to setup mode" and pressing enter, I can go into Setup Mode for Secure Boot Status)

[/FONT]
[FONT=arial]Startup

[/FONT]
[FONT=arial]Current Boot Sequence

[/FONT]
[FONT=arial]USB FDD
USB KEY
SATA 1: ST2000DM001-9YN164
SATA 2:
SATA 3:
eSATA:
Network 1: IP4 & IP6 Realtek PCIe GBE Family Controller
Other Device:[/FONT]
[FONT=arial]Excluded from boot order

[/FONT]
[FONT=arial]USB HDD:
USB CDROM:

Page 2 (for clarity reasons)

[/FONT]
[FONT=arial]CSM: Disabled (Option: Enabled)
Boot Mode: Auto (Option: UEFI only, Legacy only)
Boot Priority: Legacy first (Option: UEFI first)
Quick Boot: Enabled (Option: Disabled)
Rapid Boot: Disabled (this cannot be changed)
Boot Up Num-Lock Status: On (Option: Off)
Keyboardless Operation: Enabled (Option: Disabled)

That's the current configuration I have. [/FONT]

---

### Post by rai_shu2 on 2013-08-25
Looks like you'll need to change the Boot Sequence if you want to run off of an external drive (USB HDD, right?).

---

### Post by ndiniz on 2013-08-25
Yes! That's correct. By the way, where should I put the bootloader? I intend to put 2 linux distributions on this external drive.

---

### Post by rai_shu2 on 2013-08-25
I think boot loaders only work on one drive, so you'll definitely want that on the same (external) drive.

---

### Post by ndiniz on 2013-08-25
Since the boot loader will be on the external drive, there will be some text editing I need to do in order for my external drive to recognize I have Win8 installed. What do I need to do in order to let my external drive know I have Win8 installed?

---

### Post by rai_shu2 on 2013-08-26
The way I recall it, "Easy" install was just that (no scripting or anything required). Now, if you manually partition your setup, you'll have to make a mount point (like /windows or something) for your drive in the custom partitioner.

---

### Post by ndiniz on 2013-08-26
I will need to manually partition my external drive. What are some good free software programs to use, and what would a good partition table be for the entire drive?

---

### Post by ndiniz on 2013-08-27
I have thought about using WinGRUB. Is this a good program to use in Windows?

---

### Post by rai_shu2 on 2013-08-27
Actually, the installer on the live CD (Ubiquity) can handle all that. The live CD also includes gparted if you want to do all the partitioning in a separate application.

---

### Post by ndiniz on 2013-08-29
By the way, I do know the difference between MBR & GPT. However, since there are no current partitions on the drive (and I know the drive is clean) EASE US partition manager shows the disk type as MBR. Would it be a good thing to install it on this type of disk?

---

### Post by rai_shu2 on 2013-08-29
If there's nothing you want to keep on the drive, then you can simply ignore whatever partitions it has. In fact, I normally just delete all the partitions on drives that I intend to do a full install on. Like I mentioned before, Live CD/USB has its own partition manager and will just partition and format whatever you need and/or indicate.

---

