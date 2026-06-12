---
title: "Installing on second disk drive"
date: 2014-02-27
forum: New to Ubuntu
---

### Post by bluebedouin on 2014-02-27
I have an old hard drive from a previous computer installed in my present one which I use as a storage for my pictures.(I wiped the old os system from it.)
Is it possible to install the lubuntu iso I just downloaded to my C drive (existing hard drive with windows xp home) on to the E drive (old hard drive) so that when I first boot up I can choose which os to use? If so,how?
[ATTACH=CONFIG]250736[/ATTACH]

---

### Post by bluebedouin on 2014-02-28
129 views & no one can help? :(

---

### Post by ibjsb4 on 2014-02-28
Why change it in bios?  Just change the boot order.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=change+boot+order&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=change+boot+order&sa=Search&cof=FORID:9)

---

### Post by sudodus on 2014-02-28
Maybe someone can help. Anyway, welcome to the Ubuntu Forums :-)

In principle, yes, you can install Lubuntu to another and separate disk (not the first one), and the computer can boot from it, or boot from the first drive and then boot Lubuntu from that drive. But it also depends on your computer. So give us a chance to give relevant advice (not only guess) by specifying your computer, at least

- Brand name and model
- CPU
- RAM (size)
- graphics chip or card
- wifi chip or card
- (CD or DVD read/write or read only -- *Edit*: I looked again at the attached picture and it is DVD RW)

- (Present operating system -- *Edit*: I looked again and saw it is Windows XP).

If you intend to use a USB pendrive to install the system, please start by reading this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by ibjsb4 on 2014-02-28
> **sudodus said:**
> Maybe someone can help. Anyway, welcome to the Ubuntu Forums :-)

So give us a chance to give relevant advice (not only guess)

I was feeling lucky this morning :D

---

### Post by oldfred on 2014-02-28
If using the grub2 boot loader you can directly boot an ISO on one hard drive and install to another hard drive. But not from Windows. I now use this for all my installs as I have several hard drives. But I used similar procedure to boot flash drive which usually are seen as another hard drive.

       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by bluebedouin on 2014-02-28
> **sudodus said:**
> Maybe someone can help. Anyway, welcome to the Ubuntu Forums :-)

In principle, yes, you can install Lubuntu to another and separate disk (not the first one), and the computer can boot from it, or boot from the first drive and then boot Lubuntu from that drive. But it also depends on your computer. So give us a chance to give relevant advice (not only guess) by specifying your computer, at least

- Brand name and model Mesh   
- CPU
- RAM (size)
- graphics chip or card
- wifi chip or card
- (CD or DVD read/write or read only -- *Edit*: I looked again at the attached picture and it is DVD RW)

- Present operating system (Windows XP or something else).

If you intend to use a USB pendrive to install the system, please start by reading this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Thanks for the responses so far.Sorry for the lack of information.

Okay,I downloaded lubuntu-13.10-desktop-i386.iso & saved the file to my C drive.I want to install it on the E drive as the operating system.How do I do that?

Mesh Matrix XP 1800
AMD Athlon(tm) 64 X2 Dual
Core Processor 3800+
2.00GHz, 1.00 GB of RAM
Physical Address Extension

Microsoft Windows XP
Home Edition
version 2002
Service Pack 3

---

### Post by sudodus on 2014-02-28
You did not describe the graphics chip/card. Maybe there is only wired internet (no wifi). Otherwise I would say that the computer should run well with Lubuntu.

The safest way would be to ***disconnect the first drive***, the one with Windows. Then there is no risk, that you will overwrite or even touch it in the installation process.

What about the data on the second drive, which will be the target drive for the installation? Can it be completely overwritten, or do you have data on it, that must be kept there, because you have no other place for it? ***Installing operating systems is risky, so you might destroy the data*** (but if it is 'only' backup of data from the internal drive, and the internal drive is disconnected, it should be OK). It is a good idea to discuss how to keep your data safe, and make them safe, before starting the installation: ***Backup***!

Check that the download was correct with the md5sum according to [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

with the tool [http://www.md5summer.org](http://www.md5summer.org)

You can use a CD/DVD disk as well as a USB pendrive for the Lubuntu installer. It is important to burn or flash the iso file to the target (CD/DVD/USB) device. Do not make a regular copy of the iso file and store it as a file in a file system on the target.

***USB***: See for example [Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/") in order to make a USB install drive with ***Unetbootin***.

More details are described in this link [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)[I][B]

CD/DVD[/B][/I]: Burn a disk with for example the tool ***ISO recorder*** suggested in this link [http://www.techspot.com/blog/120/burn-iso-files-in-windows-xp-and-vista-with-ease/](http://www.techspot.com/blog/120/burn-iso-files-in-windows-xp-and-vista-with-ease/)

I'm thinking of [ISORecorder V2 - for Windows XP SP2/SP3 and Windows 2003]("http://isorecorder.alexfeinman.com/v2.htm") because you have XP SP3.

Use a temporary boot menu (if available via a hotkey, for example F12, can be different) or change the boot order in the BIOS menu system in order to boot from the CD/DVD or USB drive.

---

### Post by bluebedouin on 2014-02-28
> **sudodus said:**
> You did not describe the graphics chip/card. 
Sorry,don't know how to find that information.
> Maybe there is only wired internet (no wifi). 
The computer is wired into a router.
> What about the data on the second drive, which will be the target drive for the installation? Can it be completely overwritten, or do you have data on it, that must be kept there, because you have no other place for it? 
It has all my pictures on it & nowhere else I can store them.Would I need to partition that disk first to allow for the install?


> 
You can use a CD/DVD disk as well as a USB pendrive for the Lubuntu installer. It is important to burn or flash the iso file to the target (CD/DVD/USB) device. Do not make a regular copy of the iso file and store it as a file in a file system on the target.

From what I understand then,it isn't just a case of opening the downloaded file,clicking 'install' & letting it install in a chosen place?:shock:

---

### Post by sudodus on 2014-02-28
> **bluebedouin said:**
> Sorry,don't know how to find that information.

You can find it via the Control Panel in Windows. I don't remember exactly the menu items. But on the other hand, you can ***try Lubuntu*** booting from the CD/DVD/USB drive without installing anything, and find out if and how it works :-)
> 
The computer is wired into a router.
Good, makes it easier.> 
It has all my pictures on it & nowhere else I can store them.Would I need to partition that disk first to allow for the install?

This is a problem. You have to edit the partition, shrink it and create space for a root partition and a swap partition to be used by Lubuntu. And it is risky. It works well 95% of the times, but you may have bad luck, for example a power outage during the process (and no battery), or make a mistake.

So I suggest that you abstain from this adventure until you can get another drive, a pendrive with at least 8 GB, or and old HDD from a computer ready for recycling.
> 
From what I understand then,it isn't just a case of opening the downloaded file,clicking 'install' & letting it install in a chosen place?:shock:

No, you must boot from the installation media to make the installation. And you must edit the partition table. It is a similar procedure to install the Windows operating system. This is very different from installing a program into an existing operating system.

-o-

It is a good time to start now, because Windows XP will reach end of life in April. After that there will be no more security updates, and we can expect attacks from people who take advantage of security holes that will be revealed but not patched. So before April, you should be running Lubuntu (or some other linux distro) and be ready to live without XP, at least when connected to the internet.

---

