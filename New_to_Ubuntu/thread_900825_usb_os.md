---
title: "usb os"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by Yudraciell on 2008-08-25
Well, i wasnt sure how to title this but here i go.

I want to put ubuntu on a usb (and use it as a hard drive) like an external make it a bootable from any computer (my friends have vista and i use their computers)but i cant stand vista so i want to make a usb hdd like thingy to use ubuntu without changing their computers or putting in a cd... (if i did that his parents would flip and be like ur banned get out of house)

I have a 4 gig usb that has enough space to install and do whatever...i just want to use it like a live cd that saves like a hdd


tyvm in advance

---

### Post by tuxulin on 2008-08-25
i have never test linux on a usb but you can try this
[http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html)


Tuxulin

---

### Post by damis648 on 2008-08-25
On your computer, disconnect your hard drive(s) and boot the liveCD. Choose to "Use Entire Disk" on the flash drive, and contine through. When you get to the last step (before it actually starts installing), choose "Advanced Options", and set to install the bootloader to the flash drive (SDA Probably), and remember, the whole DRIVE, not just the partition. Good luck!

If that doesn't work, you can have a look at pendrivelinux.com

---

### Post by LLauranzonIII on 2008-08-25
> **damis648 said:**
> On your computer, disconnect your hard drive(s) and boot the liveCD. Choose to "Use Entire Disk" on the flash drive, and contine through. When you get to the last step (before it actually starts installing), choose "Advanced Options", and set to install the bootloader to the flash drive (SDA Probably), and remember, the whole DRIVE, not just the partition. Good luck!

If that doesn't work, you can have a look at pendrivelinux.com

i agree with the pendrivelinux.com option.

here is for ubuntu:

[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)

there are also the other flavors listed on there.

---

### Post by Yudraciell on 2008-08-28
but what about driver support...if i use it in my friends laptop then another persons laptop with another wireless card wont that screw things up???

---

### Post by worx101 on 2008-08-28
I know this works, don't know the exact steps but at least I can point you in the right direction.  so you might want to google it.

Just take the ubuntu live cd ISO and extract it's contents to your thumbdrive(believe the filesystem has to be fat32 for syslinux to work)
then use syslinux to make it bootable...  and thats pretty much it :)

it will work just like the live cd from then on...  its how i use ubuntu on my EEEpc :)

---

### Post by bumanie on 2008-08-28
+1 for the pendrive linux tutorials. I have installed ubuntu to both a pendrive and an external/portable hard drive following the instructions and both work fine.

---

### Post by DemonBob on 2008-08-28
Hook up the usb drive. 

Set to boot to CD, USB, then HDD in the bois

Boot the livecd 

Go through the install partitioning the usb and such. 

On the last page before you click the install button, click advanced options. 

Make sure the boot loaders is being installed to the USB Drive. 

My internal drive with the livecd was /dev/sda, externial was /dev/sdb. This may different for you so pay attention in the partitioner, or open up a terminal and do an fdisk -l to see /dev/sdx is your other partion, it shoud list ntfs or such beside it. 

I selected /dev/sdb not /dev/sdb1. The bootloader has to be installed on the disk itself not inside the partition. 

Go head and finish the install.

Upon first boot: It may fail if it does, press e to edit the boot command line for the first option change root (hd1,0). to root (hd0,0), press b to boot after the command is edited. 

Once booted, sudo gedit /boot/grub/menu.lst, and edit the root lines for the entries to correspond with the change earlier. This will make it perminiant. 


This allows me boot to Ubuntu on my externial, if you need to get back to windows, or your other os, just reboot, unplug the usb drive and it should continue to boot to your other os.

---

### Post by C.S.Cameron on 2008-08-28
I've been booting Ubuntu from thumbdrive for a couple years now.
I just install it the same as to hard disk.
4 GB will work for Ubuntu but does not leave much room.
I understand that you can keep your home folder on a separate thumbdrive.
EEExubuntu fits on a 2 GB thumbdrive and seems to work on every computer that I can get to boot from usb.

---

### Post by sofamensch on 2008-08-30
(1) You can use a LiveUSB Stick, just like a LiveCD with persistent changes. This will definetly run your linux on almost any computer, since hardware is detected on each start.

(2) You can install it like on a hard disk. This should work on different computers also, but it probably not intented to.
ATM i am having problems with Intrepid on USB, so stick to Hardy for that.

---

### Post by feelie88 on 2008-08-30
erm, i just found out that installing linux on a pendrive can drastically shorten it's lifetime so i don't actually plan on installing linux this way. sorry for wasting the forum space.

---

