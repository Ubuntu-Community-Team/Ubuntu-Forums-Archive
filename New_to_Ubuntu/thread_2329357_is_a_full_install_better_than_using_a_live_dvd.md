---
title: "is a full install better than using a live dvd"
date: 2016-06-30
forum: New to Ubuntu
---

### Post by langlang420 on 2016-06-30
hello all. brand new to Ubuntu. using the live cd of 16.04 mate to try to recover data from a external hard drive that's not showing. all was going well until I got an error message saying there was no space left to download the packages. after that, nothing but more error messages and frustration. my question is would it work better to do a full install either to the c drive alongside windows or full install to another external drive.

---

### Post by sudodus on 2016-06-30
Welcome to the Ubuntu Forums :-)

Yes! A live DVD is good for testing how it works in your computer and for installing, but you cannot save anything, no updates of the system and no data unless you save them in another drive (which is not very convenient). You can also consider creating a USB boot drive and use it similar to a live DVD or as a *persistent* live drive. And a USB drive can be re-used many times.

Ubuntu and the Ubuntu flavours (Kubuntu, ...) and intended to be *installed*. See also the following link

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

-o-

But if you use Ubuntu MATE only in order to rescue another system - it is a good idea to use a live DVD. But you must save the files somewhere else

- in an[other] external USB drive (hard disk drive or SSD)
- in a USB pendrive (but it is usually smaller and less reliable because of wear of the memory cells).

Everything that is stored in 'the system itself' is actually stored in the volative RAM, which will be gone after shutdown or reboot.

---

### Post by langlang420 on 2016-06-30
okay. I'm a little confused. as I said the packages were going well until it said no more space was left. where are the packages being downloaded when using a live cd?

---

### Post by sudodus on 2016-06-30
In the [RAM](https://en.wikipedia.org/wiki/Random-access_memory) <-- Link to Wikipedia

---

### Post by langlang420 on 2016-06-30
got it. and thanks for the help. one other thing, I'm a little wary of trying to install it on my c drive, don't wanna screw up windows and make more problems. would doing a full install to an external drive work without issue?

---

### Post by sudodus on 2016-06-30
It depends on your computer hardware (it is a good sign that the live MATE system is working well), and it depends on how Windows is installed.

Newer Windows installations made by the manufacturer or vendor are usually in UEFI mode, which can make it more difficult to install a system alongside Windows (internally or externally).

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

- and version of Windows

This makes it easier to give good advice.

- Are you intending to use Ubuntu MATE regularly, or only in order to rescue files temporarity?

***1. use Ubuntu MATE regularly***

If you intend to use Ubuntu MATE regularly, you can consider installing it into the internal drive alongside Windows, but it is very important to start with a ***backup*** - of the whole system or at the very least all your personal files and Windows recovery disks - because things can go wrong.

An alternative is to ***remove*** (at least disconnect) ***the internal drive*** during the installation of Ubuntu MATE into an external drive. That way the installation will not touch the internal drive. Backup the new Ubuntu MATE system, and keep the backup up to date.

If UEFI, you can start with this link and links from it:

[Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

***2. mainly use Windows and seldom use Ubuntu MATE***

Otherwise you can get along with a persistent live system installed by mkusb according to these links:

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

You can install mkusb into the live Ubuntu MATE system and store the iso file in another drive for the installation of a live system to work. This is only a temporary installation (into RAM) but it is enough for creating a persistent live USB pendrive.

If you want a portable installed system, and have a 64-bit CPU in your computer, you can try an installed system, that boots both in UEFI and BIOS mode according to the following link: [Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

Backup the new Ubuntu MATE system, and keep the backup up to date.

---

### Post by ian-weisser on 2016-06-30
> **langlang420 said:**
> I'm a little wary of trying to install it on my c drive, don't wanna screw up windows and make more problems. would doing a full install to an external drive work without issue?

It might be easier to simply install a Virtual Machine, and experiment with Ubuntu on the VM.
That won't mess up your Windows install.

Windows does not support dual-booting, and does not make it easy. Be prepared for the worst: A complete Windows reinstall with all data  lost. If you wish to keep Windows, then I recommend waiting until you have the proper toolkit before trying to dual-boot: Windows recovery stick, your Windows Product Key, a complete data backup, a proper Ubuntu install USB, and an uninterrupted afternoon.  

Then you are ready to learn how to repartition and dual-boot...

...though, honestly, I find it easier to install and run what I need in a VM rather than muck about with UEFI and partitioning and boot-repair and GRUB.

---

### Post by langlang420 on 2016-06-30
thanks for the detailed rundown. I mostly use a mac mini for everyday stuff and dj software and whatnot. I have a laptop mostly as a backup comp and for situations like this. I guess I would mostly be using windows more than unbuntu, if I decide to install. the specs of my system are acer aspire, forgot the model number. 2.6 ghz, 4 gigs of ram, nividia graphics card and running windows 7.

---

### Post by sudodus on 2016-06-30
Then I suggest that you focus on a system in a USB drive (a fast USB 3 pendrive, HDD or SSD), or if you have an eSATA port, you can connect that way.

Window 7 is usually not installed in UEFI mode, so I think you will not have that problem.

The first step might be to create a ***persistent live drive*** as I described in my previous post (post #6).

Later on you might try an installed system in that drive (or another USB pendrive that is big and fast enough).

-o-

A virtual machine (in VirtualBox inside Windows) can be a good alternative. With this computer I think it will be rather slow, but it will work.

---

### Post by langlang420 on 2016-07-03
oh hell! I'm done. trying to figure how anyone gets anything done with this system. put the Ubuntu mate on a usb stick and just as always can't get the software packages to complete. if I understand correctly the ram is used to store things, so if you have limited ram, as I do, 4 gigs, it seems you will never get these packages completed with the software you need. unless somebody has a workaround.

---

### Post by sudodus on 2016-07-03
You can get an installed system into a USB stick 'without too much effort' like this, as a start. Later on you can use more complicated methods.

1. Download a compressed image file of an installed mini system and check that the download was good.

2. Install mkusb into a simple live Ubuntu based system (with your limited RAM).

3. Use mkusb to install from the compressed image file to the USB stick.

4. Boot into the USB stick. Now you have a system with simple menus. You can select which desktop environment you want via a menu and reboot, for example Ubuntu MATE.

5. Expand or 'grow' your partition and file system with gparted, so that you use the whole USB stick.

6. Install your favourite program packages and tweak the system to what you want.

7. Make a backup of your system, and get a routine to backup the whole system, part of it or at least your personal files with regular intervals.

See these links and links from them with more details,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

