---
title: "How do I preserve or recreate my (I think is grub) dual boot"
date: 2020-10-17
forum: New to Ubuntu
---

### Post by Odense on 2020-10-17
I wanted to upgrade my Ubuntu to the latest LTS (Ubuntu 18.04.5 LTS > Ubuntu 20.04.1 LTS) but first got a warning that I would have to remove some ppa's


After I removed the kazam ppa the update was able to start - but stopped again after a while. I rebooted and tried again and it stopped again.
After another reboot get to the gnome classic desktop I prefer but it does not react to the keyboard, the mousepad or the USB mouse I normally use so I cannot even log on.
If I can get most of my own data out first I am OK with formatting the partition and starting again but I am running the Ubuntu as a dual boot machine where I get a menu where I can pick if I want to boot as a Ubuntu computer (default choice) or as a Windows 10 laptop.

The (I think grub) menu is on the Ubuntu partition (I select it in the bios that it should boot from the Ubuntu disk to get the menu) and will be erased if I format this partition.

How do I preserve or recreate my dual boot setup?

---

### Post by CelticWarrior on 2020-10-17
Is your computer so old that you had to do a BIOS installation? With the newer UEFI system in UEFI mode there's no such problems.

If it really is BIOS/Legacy with Windows and Ubuntu in different drives (and Ubuntu was installed as recommended in such cases -> Grub installed in the MBR of the same drive where Ubuntu is) just changing the drive boot order will allow booting Windows directly, so no problem there.
Either way, reinstalling Ubuntu will reinstall Grub correctly and recognize Windows as before.

---

### Post by Odense on 2020-10-17
> **CelticWarrior said:**
> Is your computer so old that you had to do a BIOS installation? With the newer UEFI system in UEFI mode there's no such problems.

If it really is BIOS/Legacy with Windows and Ubuntu in different drives (and Ubuntu was installed as recommended in such cases -> Grub installed in the MBR of the same drive where Ubuntu is) 

I am (almost) sure it is a computer with UEFI BUT the (too small disk) is divided into two partitions and Ubuntu is installed on its own partition.

[QUOTE=CelticWarrior;13993319
[COLOR=#000000]If it really is BIOS/Legacy with Windows and Ubuntu in different drives (and Ubuntu was installed as recommended in such cases -> Grub installed in the MBR of the same drive where Ubuntu is) just changing the drive boot order will allow booting Windows directly, so no problem there.[/COLOR]

Yes changing the drive boot order does allow booting Windows directly and that is what I am using to post this. But I prefer to use Ubuntu for most thing so would like that to work too.

> **CelticWarrior said:**
> Either way, reinstalling Ubuntu will reinstall Grub correctly and recognize Windows as before.[/COLOR]

So JUST installing Ubuntu on a freshly formatted partition will make a grub menu where I get to choose ifI want to boot to windows or Ubuntu WITHOUT needing to change boot order in the Bios or UEFI (which is a PITA to do)?

---

### Post by CelticWarrior on 2020-10-17
Obviously you need to change the order back to the drive where Grub is installed and that should be done BEFORE reinstalling Ubuntu otherwise it'll will replace the Windows bootloader in the other drive.
And that is basic knowledge for any user installing OSes. How can accessing BIOS to change ONE setting by such a PITA? Really? Or is this another joke like in your other thread?

---

### Post by T6&amp;sfpER35% on 2020-10-17
this is getting harsh , i'm staying out of it lol

---

### Post by CelticWarrior on 2020-10-17
> **3nd said:**
> this is getting harsh , i'm staying out of it lol
Not really.
With some luck it actually saves some people from themselves and future readers benefit from the implicit warnings.

---

### Post by Odense on 2020-10-17
> **CelticWarrior said:**
> Obviously you need to change the order back to the drive where Grub is installed and that should be done BEFORE reinstalling Ubuntu otherwise it'll will replace the Windows bootloader in the other drive.
And that is basic knowledge for any user installing OSes. How can accessing BIOS to change ONE setting by such a PITA? Really? Or is this another joke like in your other thread?

You are right that "you need to change the order back to the drive where Grub is installed and that should be done BEFORE reinstalling Ubuntu otherwise it'll will replace the Windows bootloader in the other drive".

You are however very wrong that "And that is basic knowledge for any user installing OSes" Most people would not know this and yet have no trouble installing Windows on their PC. The same people have never been checking their BIOS settings.

I did ask for help on a specific matter and that was the best way to preserve / recreate my dual boot (without needing to enter the bios each time boot). If you don't want to answer that because you think I should enter the bios each time) that is up to you.

---

### Post by CelticWarrior on 2020-10-17
> [COLOR=#000000]Most people would not know this and yet have no trouble installing Windows on their PC. [/COLOR]
Most people installing Ubuntu ONLY will have no trouble either.
The "trouble" comes when people want to dual-boot for which another set of knowledge/skills is really required, there's no way around it.

---

### Post by T6&amp;sfpER35% on 2020-10-17
> [COLOR=#000000]The "trouble" comes when people want to dual-boot for which another set of knowledge/skills is really required, there's no way around it.[/COLOR]
+1

to be honest(and i'm almost ashamed)i don't even know if my system is BIOS or UEFI , just popped in the ubuntu iso and installed ,deleting windows, followed the prompts and never looked back

---

### Post by oldfred on 2020-10-17
UEFI systems present two ways to boot live installer. One usually is clearly UEFI:XXXX and other just XXXX which then is BIOS boot. Mine is [noparse]UEFI:PMAP[/noparse] and PMAP, the XXXX often is name or label of flash drive.
How you boot live installer for Ubuntu or Windows installer UEFI or BIOS is then how it installs.

You used to be able to tell how you have booted Ubuntu installer as it used Syslinux for BIOS and grub for UEFI.
Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

But now with 20.10 grub is used for both UEFI & BIOS boot. You just have to check:
if test -d /sys/firmware/efi; then echo efi; else echo bios; fi
or:
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

Also some tools to create live installer, may make one that is BIOS only or UEFI only. So you have to select correct way to make UEFI installer.
Typically UEFI/gpt is UEFI.
CSM is BIOS.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

I also like to suggest gpt partitioning with Ubuntu. You do have to have MBR(msdos) if you have or want Windows installed in BIOS boot mode on same drive.
But I have used Ubuntu on a gpt partitioned drive since 2010 without issue (back then XP was on MBR drive).
Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drives since Windows 8 in 2012.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by Odense on 2020-10-18
I certainly made several mistakes.
I decided to do a fresh install which worked until I tested Windows 10.
After testing the Windows 10 partition the Ubuntu partition does no longer load the kernel but ends with grub > So now my freshly installed Ubuntu is inaccessible to me
I tried reading the great answer from oldfred but I can't completely follow the explanations in the link.

So how do I get my Ubuntu to load again?
If possible I would really prefer if I got a grub menu where I can select if I want to boot the Ubuntu partition or the Win10 partition?

---

### Post by CelticWarrior on 2020-10-18
In BIOS/Legacy installations dual-booting with Windows 10 is often a problem when Windows install those lengthy updates that require one or more reboots. So, make sure that Windows Fast Startup is OFF (you may need to check that setting more than once because sometimes Windows re-enables it) and - bummer - make sure that you boot Windows as many times necessary to finish ALL the updates installations it is doing. Just rebooting to Ubuntu after an unfinished Windows updates installation results in all sorts of errors: "grub rescue", "hdd outside of boundaries" (or similar) and even "kernel panic". However, after booting Windows as many times as needed to finish those updates, making sure again that Fast Startup was OFF and shutting down Windows, then everything worked as expected.

And yes, obviously you can have a Grub menu and from there boot both OSes in BIOS/Legacy or UEFI. That's the case of the above example and that story happened yesterday. So, before further considerations, what we can learn from this experiences is that we shouldn't do BIOS/Legacy installations unless we absolutely have to, i.e., on a BIOS machine. The problems described above have to do mostly with the MBR - mandatory for Windows systems in BIOS mode - and how modern Windows deals with that partitioning table (badly).

Almost all computers from the last decade or so are UEFI but there are exceptions. The above example is a 2014 System76 laptop purposefully "crippled" with BIOS firmware because Linux people sometimes like to show the world that they too can be dumb (and do a very fine job at that). Among other problems it prevents enabling hybrid graphics (Intel + Nvidia) and typically kills the battery in less than two years. Now, with Windows in dual-boot and MBR, it needs and hour or so of maintenance (Windows maintenance) for the occasional use of Windows which then starts the whole updates ordeal that must be finished to Windows content otherwise nothing else works. This machine also has MXLinux that is equally affected by the unfinished Windows installations and everything is booted from Ubuntu's Grub menu. So, it's not a Ubuntu's problem in this case. It's entirely Windows' fault due to the way it deals with partitions/partitioning table while it expectes a reboot to finished the updates installations. You know they're finish when the options for "reboot" or "shutdown" are just that instead of "install updates and...".

---

### Post by oldfred on 2020-10-18
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Odense on 2020-10-18
Here is the link
[https://paste.ubuntu.com/p/Z7nQDhsfqW/](https://paste.ubuntu.com/p/Z7nQDhsfqW/)

---

### Post by oldfred on 2020-10-18
See line 330.
You need Ubuntu live installer in UEFI boot mode and always boot in UEFI boot mode.
Default boot mode setting in UEFI/BIOS for UEFI is only for installed systems. You choose either UEFI or BIOS each time you boot live installer or your Windows repair flash drive. And repairs are done in the mode you boot, so always UEFI.

You have grub installed in gpt's protective MBR for BIOS boot. But also show UEFI boot files in Ubuntu install.
Never boot in BIOS mode or it will  use grub in MBR and fail.

Drive is gpt, so Windows only boots in UEFI boot mode.

Not sure if it is because you have Boot-Repair in BIOS mode or not, but you show no UEFI boot entries.
See line 115, that should have both Windows & ubuntu entries.
run this to see what it shows after you reboot live installer. You may have to install efibootmgr.
sudo efibootmgr -v

Best to run Windows repairs with your Windows repair flash drive. But you may be able to just add a Windows boot entry with efibootmgr.
And you can use efibootmgr to add an Ubuntu boot entry. Or a total reinstall of grub which uses efibootmgr to add entry. 

If systems otherwise correct:
sudo efibootmgr -c -w -L ubuntu -l "\EFI\ubuntu\shimx64.efi"  -d /dev/sda -p 2
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/sda -p 2

---

### Post by Odense on 2020-10-19
Thank you for answering oldfred.

Unfortunately I do not understand most of what you are saying. I hope you can (and will) give the instructions in simple steps. I will try to ask more specific questions also.

> **oldfred said:**
> 
See line 330.


I read the line / but what does it mean?

> **oldfred said:**
> 
You need Ubuntu live installer in UEFI boot mode and always boot in UEFI boot mode.
Default boot mode setting in UEFI/BIOS for UEFI is only for installed  systems. You choose either UEFI or BIOS each time you boot live  installer or your Windows repair flash drive. And repairs are done in  the mode you boot, so always UEFI.


I can take a picture of my bios options when I boot after posting this and upload the pic later if that helps?


> **oldfred said:**
> 
You have grub installed in gpt's protective MBR for BIOS boot. But also show UEFI boot files in Ubuntu install.
Never boot in BIOS mode or it will  use grub in MBR and fail.

Drive is gpt, so Windows only boots in UEFI boot mode.

Not sure if it is because you have Boot-Repair in BIOS mode or not, but you show no UEFI boot entries.
See line 115, that should have both Windows & ubuntu entries.
run this to see what it shows after you reboot live installer. You may have to install efibootmgr.
sudo efibootmgr -v


I will try using the command in a terminal

but how do you see if this (line 113/116) is Ubuntu or Windows
BIOS is EFI-compatible, but it is not setup in EFI-mode for this live-session.
EFI in dmesg.
[    0.012802] ACPI: UEFI 0x0000000077EF7000 000042 (v01 LENOVO CB-01    00000001 ACPI 00040000)
[    0.012822] ACPI: UEFI 0x0000000077EF9000 000236 (v01 LENOVO CB-01    00000001 ACPI 00040000)

> **oldfred said:**
> 
Best to run Windows repairs with your Windows repair flash drive. But  you may be able to just add a Windows boot entry with efibootmgr.
And you can use efibootmgr to add an Ubuntu boot entry. Or a total reinstall of grub which uses efibootmgr to add entry. 


I do not have a Windows repair flash drive but I can try to get hold of another empty USB stick and make one after I googled for it. 
How do I use efibootmgr?
How do I do a total reinstall of grub?

> **oldfred said:**
> 
If systems otherwise correct:
sudo efibootmgr -c -w -L ubuntu -l "\EFI\ubuntu\shimx64.efi"  -d /dev/sda -p 2
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/sda -p 2


How do I know if systems are otherwise correct?

I do not mind reinstalling Ubuntu since I have the live stick and it is a fresh install anyway. I would prefer to avoid reinstalling Win 10 though.

---

### Post by oldfred on 2020-10-19
Your UEFI should have two ways to boot USB flash drive with Ubuntu live installer on it.
But some tools to create live installer may make either UEFI or BIOS/CSM version, not both. So how did you make live installer? If a choice it must be UEFI.

My UEFI shows UEFI: PMAP or PMAP as boot options. The UEFI one is clearly for UEFI boot. Where I have PMAP, it often is the name or label of the flash drive.

Boot-Repair's advanced mode is probably the easiest way to do a full reinstall of grub (link with screen shots in post #13, if you looked at it). You can do a chroot from live installer & mount partitions, so updating installed system, not live installer. The chroot is CHange ROOT.

---

### Post by Odense on 2020-10-19
> **oldfred said:**
> Your UEFI should have two ways to boot USB flash drive with Ubuntu live installer on it.
But some tools to create live installer may make either UEFI or BIOS/CSM version, not both. So how did you make live installer? If a choice it must be UEFI.

My UEFI shows UEFI: PMAP or PMAP as boot options. The UEFI one is clearly for UEFI boot. Where I have PMAP, it often is the name or label of the flash drive.

Boot-Repair's advanced mode is probably the easiest way to do a full reinstall of grub (link with screen shots in post #13, if you looked at it). You can do a chroot from live installer & mount partitions, so updating installed system, not live installer. The chroot is CHange ROOT.

Thank you for answering again oldfred.

I used Rufus (see attached screenshot).
When MBR is selected I can only select "BIOS or UEFI"
When GPT is selected I can only select "UEFI non CSM"
I let it stay on the default MBR as this was recommended in the manual I followed.
Should I make another with GPT chosen?


I have uploaded a pic (hopefully readable) of the boot options in my bios - what should I choose?


Naturally I looked at the link with screen shots in post #13. Otherwise I would nothave been able tomake the "boot-info summary report"
I will try reading it again with emphysis on "a full reinstall of grub".

---

### Post by oldfred on 2020-10-19
Perhaps Rufus has changed.
It used to be UEFI/gpt or UEFI's CSM with MBR.
CSM is really BIOS
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Your UEFI system is showing both Windows & Ubuntu under UEFI.
It clears has two categories, which is better than mine which just mixes them up.
My Motherboard would not boot in UEFI mode when I had Legacy or UEFI. I had to select UEFI only. But that varies by vendor.
And a few older UEFI systems, seemed to need legacy on to boot in UEFI mode. That seems backwards, but that was reported by several users.

---

### Post by Odense on 2020-10-19
> **oldfred said:**
> 
Perhaps Rufus has changed.
It used to be UEFI/gpt or UEFI's CSM with MBR.
CSM is really BIOS
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode


So is my Live stick OK (MBR and BIOS (or UEFI)) or will it work better if I make it again with GPT and UEFI's CSM?

> **oldfred said:**
> 
Your UEFI system is showing both Windows & Ubuntu under UEFI.
It clears has two categories, which is better than mine which just mixes them up.
My Motherboard would not boot in UEFI mode when I had Legacy or UEFI. I had to select UEFI only. But that varies by vendor.
And a few older UEFI systems, seemed to need legacy on to boot in UEFI mode. That seems backwards, but that was reported by several users.

So - are my BIOS settings OK or what do you recommend I change?


> **oldfred said:**
> 
Boot-Repair's advanced mode is probably the easiest way to do a full reinstall of grub (link with screen shots in post #13, if you looked at it). You can do a chroot from live installer & mount partitions, so updating installed system, not live installer. The chroot is CHange ROOT.


So I "install" Boot repair on the Live USB stick again and try to follow the full reinstall of grub in advanced mode. And it is relatively easy to

make the Ubuntu partition bootable (without ruining the now working Windows 10 partition)?

---

### Post by oldfred on 2020-10-19
If you are booting in UEFI mode, then you are ok.
You can confirm:
[ -d /sys/firmware/efi ] && echo EFI || echo Legacy
if test -d /sys/firmware/efi; then echo efi; else echo bios; fi

Booting of live installer is manually selected each time you boot.
The default setting in UEFI is only for installed systems. And if UEFI boot works, that is ok.
But if all systems are UEFI, you really do not need Legacy turned on at all.

Reinstall of grub should not modify Windows other than setting Ubuntu/grub as first in boot order.
For grub to boot Windows you do have to have Windows fast start up off.

---

### Post by CelticWarrior on 2020-10-19
The MBR setting in Rufus results in media that boots in BIOS/Legacy only. It's because of this confusing settings for newbies that I often recommend DD mode in Rufus or any other tool running DD under the hood like Balena Etcher.
I would also recommend disabling Legacy/CSM in UEFI.

This is some of the things I mentioned before. Not knowing how to navigate the firmware settings is not an option for dual-booting nowadays.

---

### Post by Odense on 2020-10-19
> **oldfred said:**
> 
If you are booting in UEFI mode, then you are ok.
You can confirm:
[ -d /sys/firmware/efi ] && echo EFI || echo Legacy
if test -d /sys/firmware/efi; then echo efi; else echo bios; fi


This is the command I can paste into a terminal window after booting on the USB stick - do I paste them one line at a time?

[ -d /sys/firmware/efi ] && echo EFI || echo Legacy
if test -d /sys/firmware/efi; then echo efi; else echo bios; fi



> **oldfred said:**
> 
Booting of live installer is manually selected each time you boot.
The default setting in UEFI is only for installed systems. And if UEFI boot works, that is ok.
But if all systems are UEFI, you really do not need Legacy turned on at all.


I will try selecting UEFI only

> **oldfred said:**
> 
Reinstall of grub should not modify Windows other than setting Ubuntu/grub as first in boot order.
For grub to boot Windows you do have to have Windows fast start up off.

Before I ruined my Ubuntu installation by some wrong choices I had a grub menu(when the Ubuntu partition was first boot priority in BIOS). Since the Windows partition is unchanged I think it should still work.

---

### Post by CelticWarrior on 2020-10-19
Make sure to redo your USB and if using Rufus either select GPT/UEFI or use DD mode.
As it is now it won't boot once you disable Legacy.

---

### Post by oldfred on 2020-10-19
You do have good backups?
Then a quick user mistake is not the end of the world. I have made mistakes, silly keyboard did what I told it, not what I wanted. :(

You should not make any major system changes without updating your normal back up of all your data. 
With Ubuntu I prefer to just backup my data, settings & list of apps as it is easy to reinstall. But Windows is not as easy to install, so whatever Windows users recommend then would be best way to back up Windows.

---

### Post by CelticWarrior on 2020-10-19
For Windows is basically the same: Backup your data (personal files) and previously download all the required and updated drivers as well as the installers for all the third-party software you need; software from the Windows Store should be installed with the app.

Also keep in mind the order for the drivers installations. Unless otherwise stated by the vendor the order is always Chipset, Graphics then all the other in no particular order. There are exceptions where sound drivers must be installed before Bluetooth but those are rare. Generally speaking leave all the network stuff for last. It avoids distractions ;) Then you can go online but before anything else install all the updates (and reboot as many times needed). Finally you can do your personal "tweaks", customization, etc. and install other software.

This all takes roughly the times it would take to install Ubuntu or any other mainstream Linux distro FOUR/FIVE TIMES including the occasional additional driver. It's sad but it is what it is. That's why whenever people say "Windows is so much more advanced then [insert Linux distro]" I have to LOL.

---

### Post by Odense on 2020-10-19
> **oldfred said:**
> You do have good backups?
Then a quick user mistake is not the end of the world. I have made mistakes, silly keyboard did what I told it, not what I wanted. :(

You should not make any major system changes without updating your normal back up of all your data. 
With Ubuntu I prefer to just backup my data, settings & list of apps as it is easy to reinstall. But Windows is not as easy to install, so whatever Windows users recommend then would be best way to back up Windows.

Not so much.
But - before I try the grub install - I will make a backup of the complete harddisk with this:
[http://www.drivesnapshot.de/en/down.htm](http://www.drivesnapshot.de/en/down.htm)

IS this the commands I can paste into a terminal window after booting on the USB stick - do I paste them one line at a time?

[ -d /sys/firmware/efi ] && echo EFI || echo Legacy
if test -d /sys/firmware/efi; then echo efi; else echo bios; fi

---

### Post by oldfred on 2020-10-19
That is the same command, two different ways.
Try one and then other, but not both at same time on same line.
For multiple commands on one line you have to have && in between.

---

### Post by CelticWarrior on 2020-10-19
> **Odense said:**
> 
IS this the commands I can paste into a terminal window after booting on the USB stick - do I paste them one line at a time?

[ -d /sys/firmware/efi ] && echo EFI || echo Legacy
if test -d /sys/firmware/efi; then echo efi; else echo bios; fi

Only one is needed and any of them will give the exact same result. And that result will be "Legacy" for the first and "bios" for the second (same thing) if you use the same USB made with Rufus with MBR/"BIOS or UEFI" settings > it ONLY boots in real BIOS or in UEFI in Legacy/CSM/"BIOS" mode.
Rufus devs assume everybody knows this but in reality most don't and then mistakes happen (a lot).

The settings GPT/UEFI result in USB media that ONLY boots in UEFI mode.
Using the DD mode instead of the default options results in USB media capable of booting in both modes because the Ubuntu ISOs are hybrid. DD is what almost all the other tools under the sun use. This is the same as using optical media (DVD) but way faster.

---

### Post by Odense on 2020-10-20
> **CelticWarrior said:**
> 
Make sure to redo your USB and if using Rufus either select GPT/UEFI or use DD mode.
As it is now it won't boot once you disable Legacy.


I remade the stick with GPT/UEFI
I disabled Legacy

I tried to use both commands but it did not look like anything happened - see the attached screeshots.

After that I made a new Boot-repair info:

[https://paste.ubuntu.com/p/gBMsvKzz8V/](https://paste.ubuntu.com/p/gBMsvKzz8V/)

So - what is the next step (I DID make a full HD image as a backup)?

---

### Post by oldfred on 2020-10-20
It looks like you have a full install of Ubuntu in UEFI mode.
You do have grub in gpt's protective MBR which will not work, but otherwise does not matter as long as you never try to boot in BIOS/Legacy/CSM boot mode. As it will never work.

You can run the Boot-Repair fix which just reinstall's grub.
> The default repair of the Boot-Repair utility would purge (in order to fix packages) and reinstall the grub-efi-amd64-signed of
sda9,

---

### Post by Odense on 2020-10-20
> **oldfred said:**
> It looks like you have a full install of Ubuntu in UEFI mode.
You do have grub in gpt's protective MBR which will not work, but otherwise does not matter as long as you never try to boot in BIOS/Legacy/CSM boot mode. As it will never work.

You can run the Boot-Repair fix which just reinstall's grub.

I tried doing that - here are the screenshots

But nothing seemed to happen when I entered each command - what am I doing wrong?

---

### Post by oldfred on 2020-10-20
The chroot command are just mounting your partitions.
Then you run a full reinstall of grub command.

---

### Post by Odense on 2020-10-20
> **oldfred said:**
> 
The chroot command are just mounting your partitions.
Then you run a full reinstall of grub command.


Just with the default settings (see the attached screenshots) or what should I change?

---

### Post by oldfred on 2020-10-20
It looks like it made most of the selections automatically, or did you do that.
I might include newest grub version & newest kernel, but that may or may not be newer versions.

---

### Post by Odense on 2020-10-20
> **oldfred said:**
> 
It looks like it made most of the selections automatically, or did you do that.
I might include newest grub version & newest kernel, but that may or may not be newer versions.


It made them automatically.
I do not know what I am doing wrong - I can start it in advanced mode - and it get to the point where I am told to enter the commands in a terminal window - but then nothings seem to happen and I cannot move forward but only cancel which rolls everything back. Somehow I THINK the grub on sda9 / but I do not know what difference that makes.

[https://paste.ubuntu.com/p/FpbMw8SM3w/](https://paste.ubuntu.com/p/FpbMw8SM3w/)

Boot successfully repaired.

[https://paste.ubuntu.com/p/2SvmXJGQ6y/](https://paste.ubuntu.com/p/2SvmXJGQ6y/)

---

