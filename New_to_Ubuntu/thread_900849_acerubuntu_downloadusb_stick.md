---
title: "acer/ubuntu download/usb stick"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-25
just got an acer and it came with xp.  I want to get rid of that, and install ubuntu but there is no cdrom drive.  so I use one of those usb things?  is the format different to install from a usb or can I use the standard x86 etc download?  I only see one and they keep talking about cd image.  can ubuntu go over the top of XP?  or do I erase XP?

---

### Post by zamadatix on 2008-08-25
you dont have to erase xp you can set that to have a smaller size on the hard drive. make sure oyu defrag first. as for the usb thing oyu can google make ubuntu live usb and make one on windows the boot from it. ill look up link now.

heres the link to the ubuntu wiki on the usb thing.
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

edit: also it will install grub wich will allow you to load windows or any other s after boot. hope oyu like it (im installing ubuntu on acer right now ironic!)

---

### Post by Bradtek on 2008-08-25
It's doable (not tried it myself)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

> can ubuntu go over the top of XP? or do I erase XP? 
Ubuntu installation will give you the choice to use the whole hard drive
(get rid of Windoze) or setup a partition for itself (dual boot)

---

### Post by adamogardner on 2008-08-25
> **Bradtek said:**
> Ubuntu installation will give you the choice to use the whole hard drive
(get rid of Windoze) or setup a partition for itself (dual boo

Thank god for that! windos gotta go.

---

### Post by adamogardner on 2008-08-25
I don't get it.  isn't there a way to install ubuntu or rather download it to a usb thing and then boot my other computer with it?  that wiki is about complicating what should otherwise be easy.

i have an ubuntu cd   how do i transfer it to usb thing?

---

### Post by adamogardner on 2008-08-25
how do I make it boot from the usb drive.  i dragged and dropped my iso download into the window for the usb thing and rebooted the acer and XP started up again.

---

### Post by adamogardner on 2008-08-25
upon reboot I hit f2 and went to boot tab and changed the priority to the usb that read "sandisk" so that must be the usb device.  I exited saving changes and it still booted into xp.  bad iso?  bad computer?

---

### Post by zamadatix on 2008-08-25
usb can tboot iso... wihtotu some stuff and basically what was in the wiki. the bios is not expecting the usb to jsut hold a iso (which owuld be really simple and awesome) this is about as short as it gets [http://edoceo.com/liber/ubuntu-live-usb]("http://edoceo.com/liber/ubuntu-live-usb")

---

### Post by adamogardner on 2008-08-25
you gotts be kidding me!  this stuff is hard.  I'm supposed to type a lot of things into a terminal that I don't understand at all.  there must be a way for a dummy like me to put ubuntu in my laptop.  can I order one from somewhere?

---

### Post by adamogardner on 2008-08-25
I have a computer and can't put linux on it

---

### Post by adamogardner on 2008-08-25
whats this mean?  is this the right information for me?  

Re-partition and format the USB drive. Ensure that the first partition is at least 1GiB in size and marked bootable. Any remaining space can be divided as necessary. When formatting choose ext2, do not put a journaling filesystem onto the USB device.

cfdisk /dev/sda
mkfs.ext2 /dev/sda1
mkfs.ext2 /dev/sda2

---

### Post by adamogardner on 2008-08-26
well whats mkfs?  make file systemsd1 into file system2.  should I charge into this like I did last time and achieve boot failure?

---

### Post by adamogardner on 2008-08-26
none of this is working.  I seem to have a lot of crap on my usb thing now.  So a new question:  how do I start over?  there is too much **** I don't know what it is on my usb.  and it still doesn't boot.  this really sucks.

---

### Post by adamogardner on 2008-08-26
explain this please.  I know I'm asking a lot.  all 75 viewers have been so helpful already but I just am so confused.

Note that you don't have to burn the iso to copy it's contents, from linux it can be mounted like so:

mount -o loop /path/to/ubuntu.iso /path/to/mount/point

path is to cdrom?  no to usb from cdrom?  how is that written?  Am I even barking up the right tree?

---

### Post by adamogardner on 2008-08-26
what am I doing with "isostick.sh?"  i apted got it.  it was part of the directions.  It is on my destktop with other unknowns.  I can use wine for it it says.  So now I need wine?  I just want to put ubuntu on a little computer.  but alas I'm installing wine now which is just stupid by me, but I've been left to my own devices for 12 hours and am running out of choices.

---

### Post by markbuntu on 2008-08-26
Try this, it is a detailed explanation of how to get Ubuntu onto an aspire one:

[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by cookdn on 2008-08-26
Hi Adam,

You need a 1GB USB stick, the standard ubuntu-8.04.1-desktop-i386.iso and UNetbootin from [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/).

UNetbootin is an easy cross-platform GUI for getting the live CD ISO onto the USB stick in a bootable condition. After that you need to alter the BIOS config on your PC to boot from a USB Hard Disk.

Hope this helps.
David

---

