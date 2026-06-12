---
title: "Difficulty installing Ubuntu 18.04 LTS on Lenovo"
date: 2020-04-25
forum: New to Ubuntu
---

### Post by tjab94 on 2020-04-25
I bought a Lenovo Thinkstation S30 to use as a gaming computer and I decided to stray from Windows after years of loyalty. So after doing some research I wanted to do the Steam OS but it's more of a dedicated game system much like a regular game console. So the Steam OS uses a similar kernal to Ubuntu I believe, which I figured is good enough since Ubuntu is rather popular and my dad (a guy that repairs computers in his spare time) successfully installed it on a guest computer in his house. 

So I get 18.04 LTS on USB, extracted the files in the USB then went over to the new computer. Long story short I got Ubuntu to "work" on the computer, and it even told me the hard drive that came with the computer was about to fail, but even after getting a new WD Black 2TB HDD (which I was told is the absolute limit of what the Ubuntu OS can handle on the main HDD), it's like it's not installing on the hard drive because I can't access Ubuntu without the USB... and even then it's only the test version because it still has the option to install the system. But then what's weird is when I go to install it again it asks how I want to reinstall the system (either erase and reinstall, install 18.04 alongside 18.04... which is weird, or erase all and install). So it sees the system was installed but I can't boot from the hard drive (all it says is "Reboot and Select proper Boot device or Insert Boot Media in selected Boot device and press a key)

Everything I have found either wasn't clear, didn't work, was for different computers/BIOS, or was for newer versions of Ubuntu. But I was recommended by my dad to use the LTS version, so I got 18.04. I know about Wine and stuff I can get to run my programs from Windows 7, but I just need to get the system to boot on it's own first of course. 

I have tried booting in Legacy mode (won't even access the USB), changing boot order, even trying to add Windows Boot Manager via the Ubuntu command console in hopes thats what UEFI mode needed (all things I have found people online suggest). All to no avail. I cant say for sure it's not the fault of the motherboard but the computer looks spotless inside-out with no bloated capacitors or crusty components. No weird noises, runs silent, I'm at a loss


Computer specs:

-Lenovo Thinkstation S30

-Intel Xeon E5-1620 3.6GHz quad core CPU
-24576 MB of RAM @ 1333MHz (4GB x6)
-Western Digital Black 2TB 7200RPM HDD
-600 watt oem PSU
-EVGA Nvidia Geforce GTX 960 2GB
-TPLink N800 network adapter

(half of these things are irrelevant but this is all that's currently installed in the tower. I added the network card, video card, and replaced the hard drive)

---

### Post by DuckHook on 2020-04-25
Welcome to the forums, tjab94.

On a meta-level, Ubuntu is not a gaming OS. Since your stated goal is to use this box as a gaming computer, you may wish to re-think your strategy and stick with Windows.

That said, I happily run a number of steam games on mine. However, I've found the process to be often tricky and technical. As only one example: Civ 5 requires a kludge to limit number of CPU cores; otherwise it crashes mid game with highly obscure error messages. This doesn't happen in Windows because most of these games were never originally designed for Linux and their Linux ports are sometimes incomplete.

OTOH, if you wish to expand your computing knowledge into the geek-sphere to a level of competence that is far beyond gaming, then Linux is where it's at.

The "limitations" that someone told you about Ubuntu are false. There is no practical upper limit to HDD size in Ubuntu. The ext4 filesystem is superior to NTFS in practically every way, and if you decide to use even more up-to-date filesystems (like LVM or ZFS), they will leave MS-type filesystems eating their dust.

You may be making this more complicated than necessary. Make sure you have fastboot and secureboot disabled in your BIOS before trying to install.

Are you dual-booting with Windows? If so, you will have to wait for someone else to help. I have not dual booted with Windows since the XP days and can't guide you through the arcane setups needed for happy co-existance.

---

### Post by CelticWarrior on 2020-04-25
Welcome.

Lots to unpack here... I'll try to follow your though process. So, let's start:
> So I get 18.04 LTS on USB, extracted the files in the USB then went over to the new computer.
It's OK. This actually works for any UEFI machine. Lenovo Thinkstation S30 is UEFI so it's fine. It doesn't work for BIOS machines.
The ISO file is intended for making installation/live media and should be "burned" to a USB stick (or a DVD in the old days). When doing it from Windows, and contrary to what the official guides recommend, [Balena Etcher]("https://www.balena.io/etcher/") should be the go to software for newbies as it's virtually fool-proof. This software "copies images to drives byte by byte" so the resulting USB stick will boot anywhere, BIOS or UEFI.

> after getting a new WD Black 2TB HDD (which I was told is the absolute limit of what the Ubuntu OS can handle on the main HDD
Who told you that is seriously misinformed.
Ubuntu and any other Linux distro can handle ANY size, ALL partitioning types and several different file systems although only a few can be used for the system partitions; data partitions can be pretty much anything.

> can't access Ubuntu without the USB... and even then it's only the test  version because it still has the option to install the system. But then  what's weird is when I go to install it again it asks how I want to  reinstall the system (either erase and reinstall, install 18.04  alongside 18.04... which is weird, or erase all and install). So it sees  the system was installed but I can't boot from the hard drive (all it  says is "Reboot and Select proper Boot device or Insert Boot Media in  selected Boot device and press a key)

You need to understand UEFI, its requirements, how it boots and familiarize yourself with the firmware (UEFI) settings. UEFI is what replaced BIOS a long time ago but unfortunately some vendors kept using the same "BIOS" acronym which is incorrect.
Namely, you need to check whether or not the correct boot setting is selected. Apparently it is NOT. Please note that I'm assuming Ubuntu has been correctly installed in the internal drive so all it should need is this UEFI ("BIOS") setting correct.
The above notwithstanding you should learn some more (OK, a lot more) about how OSes in general should be installed and Ubuntu in particular:
[https://askubuntu.com/questions/6328/how-do-i-install-ubuntu](https://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
Some information and screenshots may not be current but the overall process is still valid. Complement it with the following [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
If installing in a new blank drive the automatic installer takes care of everything but if reusing a drive and/or installing a dual-boot with Windows, there are some considerations:
Windows strictly requires GPT for UEFI and MBR for BIOS/Legacy; Ubuntu isn't that strict but perhaps it should be. Anyway, there are many advantages in GPT and no reason at all not to use it unless installing Ubuntu or a dual-boot in an old BIOS computer.

> I know about Wine and stuff I can get to run my programs from Windows 7
WINE can enable running **some** Windows software, not all, and the experience varies a lot among the ones that run. If you need many of those, better to install Windows (Windows 10, of course; installing unsupported end-of-life OSes, especially of the Windows family like Windows 7 is stupid and irresponsible).

> I have tried booting in Legacy mode (won't even access the USB)
I'm really sorry you've been misinformed again. There are lots of dumb people out there, unfortunately, and the computer literacy is still very far from what should be in 2020.
UEFI machines > UEFI mode, period. And if you installed in UEFI mode, changing to other mode will make any OS unbootable. So, no, don't even think about about it. For best results and with only a few exceptions Legacy/CSM support should be disabled.
Your settings should be:
[LIST]
[*]UEFI only
[*]Secure Boot OFF
[*]Fast Boot OFF
[/LIST]


Now, to troubleshoot what's happening, we need to see details.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Follow the 2nd option in a live session (booting from the USB like you've been doing).
DO NOT CLICK "REPAIR". Click "CREATE A BOOTINFO SUMMARY" and post the resulting link so we can take a look at it.

---

