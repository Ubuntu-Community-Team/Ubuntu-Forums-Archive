---
title: "Installing Ubuntu to external USB drive?"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by rrumaner on 2008-09-09
Can I do this? Is it possible to install Ubuntu to an external USB drive and expect it to work or does it have to be installed on the primary drive?

---

### Post by snowpine on 2008-09-09
It depends on your computer's bios. If your computer is capable of booting from USB, then yes, it should work. You may have to press a key such as F2 or F12 at boot to select USB from your boot menu.

Personally, I get very paranoid with that kind of install, that I might mess up something on my main hard drive, so I actually physically disconnect the cable going to my main hard drive before installing. Probably unnecessary, but I like to be really careful. :)

Good luck!

---

### Post by cotcot on 2008-09-09
If you install it on a usb you need to use the alternate install media, because the normal media do not give you to save the boot loader somewhere else than on the MBR. 
With the alternate CD choose the first partition on usb stick instead of the MBR. Check its address with fdisk -l.

---

### Post by mlentink on 2008-09-09
> **cotcot said:**
> If you install it on a usb you need to use the alternate install media, because the normal media do not give you to save the boot loader somewhere else than on the MBR.

Yes it does.
You can easily use the graphical installer included with your LiveCD. Just remember to use the 'Advanced" button after partitioning to install GRUB on the USB drive (usually sdb or hdb). 
If you want to make the boot totally independent, you will need to change the drive designations in the /boot/grub/menu.lst file on the usb-drive, because at boot time it will not be hd1, but rather hd0.

---

### Post by C.S.Cameron on 2008-09-09
I install to both USB HDD and USB pendrive same as to HDD.
You might want a FAT partition so that you can connect to a windows computer.
I select Guided, Use Free space, when installing and leave a bit of the FAT partition. Have not had luck installing to thumbdrive using manual partitioning mode.

---

### Post by ChaosLogicZero on 2008-09-10
I have a similar question.  I have backtrack 3 and ubuntu on usb sticks, but currently can't save any changes.  What I want to do is get Ubuntu installed on one stick and backtrack on another.  Windows Vista is installed on the HD.  I don't want anything involving either of the Linux distro's instillation to alter the HD.  I want to be able to disconnect the stick and have my laptop work as though nothing has changed.  In other words, I don't want GRUB to load from the HD and don't want the bios freaking out because of the usb stick being disconnected.  If i want to boot from the usb stick i want to just manually press F12 and choose boot from usb (this is a bios boot device option).  If I want to boot into windows, I dont' want to press anything and have windows vista boot like it currently does.  Can anyone list the steps I need to take to accomplish this or post a like to steps to accomplish this?  I've looked around, but what I'm finding so far isn't saying anything about the install not touching the HD.  I also need the installs to allow changes so I can install the updates/patches for Ubuntu and Backtrack.

---

### Post by Seisen on 2008-09-10
Fedora has done it [http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo]("http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo") so its got to be possible to do it Ubuntu. Actually somebody has created a way to do it. [http://klik.atekon.de/liveusb/]("http://klik.atekon.de/liveusb/")

---

### Post by ChaosLogicZero on 2008-09-10
I tried what is shown in the ubuntu link you posted.  That does work, however even with that allowing me to save changes to my user directory, it doesn't allow any changes to Ubuntu.  For instance, I followed those steps, booted into ubuntu, connected to the internet, installed available updates.  After rebooting back into ubuntu and connected to the internet, ubuntu says the same updates need to be installed, so it isn't saving the changes made by the updates.  I thought maybe an install to the usb stick might work better, but I was afraid to try it not knowing if GRUB would be installed to the HD.

---

### Post by C.S.Cameron on 2008-09-10
Like I said, if you install to USB device the same as to HDD, you end up with a system the same as on HDD.
I have wine installed, sketchup, tvtime, etc.
When I reboot it's all just as I left it when I shut down.
I just discovered switchconf in the repositories.
This allows me to boot to multiple xorg.conf's so I can use different configuration for each computer, Nvidia drivers or generic.
If you are worried about your HDD unplug it before the installation.
You don't have to worry about your HDD booting from USB, you have to jump through a bunch of loops just to see them.
There is a the grub option to boot to first hard disk, so you don't have to unplug your stick.

---

### Post by crispy_420 on 2008-09-10
Here's an interesting tool I came across for just this type of situation:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Many distros an option as well.

---

### Post by jemate18 on 2008-09-10
Here is the LINK from UBUNTU Site itself... just follow the steps
> [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

