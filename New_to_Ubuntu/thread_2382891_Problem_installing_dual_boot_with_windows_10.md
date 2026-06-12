---
title: "Problem installing dual boot with windows 10"
date: 2018-01-18
forum: New to Ubuntu
---

### Post by dani102 on 2018-01-18
I had Windows 10 and I tried to install CentOs 7, i had a lot of problems but I did. Now I can't boot to Windows anymore. So I tried installing Ubuntu 16.04 to remove the CentOs partitions and being able to enter to windows too. But I can't install it nor prove it without installing because it is stuck on the ubuntu logo in the purple page. I checked the disk for errors and I was not able to reboot because it says the partitions sda1 and more can't mount due to windows is hibernating. But I can't enter to any O.S. so I don't know what to do. I would like to come back to windows, remove all the centOs stuff and after all of this, install safely ubuntu alongside windows. Please help! Thank you and sorry.

---

### Post by oldfred on 2018-01-18
From UEFI boot menu boot directly into Windows and turn off hibernation.
If necessary, use your Windows repair flash drive to fix Windows issues. 

You do need to have Windows fast start up or hibernation off.
Often best to have UEFI Secure boot off.
More details on UEFI installs in link in my signature.

---

### Post by dani102 on 2018-01-19
I can't boot to Windows, I can't boot to CentOs, I can't boot to Ubuntu. 
I can change things from UEFI but I don't think I can add more boot options.
So please, I don't know what can I do without booting to windows

---

### Post by oldfred on 2018-01-19
Many systems require a full cold boot, not warm reboot.
That is where you shut system down, unplug from power, if laptop remove battery, and then hold power switch for 10 sec or so to drain any remaining power (no lights, nothing).
Then see if you can boot and immediately press correct keys to get into UEFI/BIOS.

If not, you have to open system and jumper reset pins on motherboard. You have to check manual on where and what pins. That will also reset UEFI to defaults, so any changes you made, must be redone. If no pins you can also remove the small coin battery on motherboard for a bit to totally reset also.

But grub will not boot broken or hibernated Windows, so you will need to directly boot Windows. And since only one MBR with old BIOS/MBR configuration, you have to temporarily restore Windows boot loader and/or use your Windows repair disk and its repair/recovery console.

---

### Post by dani102 on 2018-01-19
OK, before removing the battery, what config the UEFI/BIOS has to have? Secure boot enable, Launch CSM disabled? something else?

---

### Post by oldfred on 2018-01-19
Windows 10 is UEFI boot, normally. Microsoft requires vendors to install in UEFI boot mode.
But if you installed yourself or upgraded from Widnows 7 it may be BIOS boot.

But then any other system you install may be either UEFI or BIOS/CSM/Legacy mode. How you boot install media, is then how it installs.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Generally better to have UEFI Secure boot off. 
Some systems (Dell) seem to want Legacy on, but still boot in UEFI mode. Most will only boot in legacy/BIOS mode if that is turned on.

What brand/model system?

---

### Post by dani102 on 2018-01-27
> **oldfred said:**
> 
What brand/model system?
I have a laptop ASUS R510V which was freeDos until I installed Windows 10, then I tried to install ubuntu but it doesn't went well. I have been able to know all about my partitions with disk part:

I have a GPT hard disk which has 9 partitions;

[COLOR=#000000][FONT=&amp]3 main partition C, D and E (basic data partition). I don't know what has E.
2 recovery partition F and G that are Windows Recovery Environment. F is raw and I don't know what it is. And G is ntfs and I think it's the Live CD.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]1 system partition of 100MB and FAT. It is the EFI System Partition. I still don't know too much about it.
1 unknow partition. The BIOS Boot Partition. I'm trying to figure out its function.
1 reservation partition (Microsoft System Recovery). The same.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]And 1 unknow partition (LVM from linux) which I supposed it has all of the linux stuff.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]
I want to know how to recover the access to Windows. (By reparing the GRUB or by reparing the Windows boot loader which I don't know where it is).[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Sorry for being late and thank you![/FONT][/COLOR]

---

### Post by oldfred on 2018-01-27
If a newer user best not to use LVM as that is an advanced logical volume management system. 
But it is required if you must have full drive encryption or manually partitioned so LVM is in a separate physical partition. 
Centos may have used LVM as its default. Ubuntu does not use LVM by default, but has it as an install option.

Windows requires a small system reserved unformatted partition.
If you install Ubuntu in BIOS boot mode, then on gpt grub needs a 1 or 2MB unformatted bios_grub partition.
Both of those are unformatted, so may show as errors in gparted, but gparted really should know they are required partitions.

Since UEFI you should be able to directly boot Windows from UEFI boot menu.

As long as Ubuntu is in BIOS boot mode, you will not be able to boot Windows from grub menu.
UEFI and BIOS are incompatible. Or once you start booting in one mode from UEFI, you cannot switch. And then grub can only boot other installs that are in same boot mode as you are booting grub.
If you want to boot systems in different boot modes, you may be able to directly boot both from UEFI menu. But some systems require you to turn on/off UEFI or BIOS/CSM/Legacy settings also.

You can also use Boot-Repair's advanced options to totally uninstall the BIOS version  of grub and install the UEFI boot version of grub.

If installing Ubuntu, just be sure to boot install media in UEFI boot mode as that is then how it installs.

Directly boot into Windows and turn off fast start up/hibernation.
Boot into Ubuntu in UEFI mode and use gparted to remove the LVM partition. Gparted will not edit LVM partitions as you have to use LVM tools, but you should be able to just delete the partition the LVM is in.

See also link in my signature for more UEFI info.

---

