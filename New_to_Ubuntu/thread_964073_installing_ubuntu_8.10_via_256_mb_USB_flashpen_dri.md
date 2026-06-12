---
title: "installing ubuntu 8.10 via 256 mb USB flash/pen drive"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by hanzj on 2008-10-30
Hello,
I want to save my CDs, so I would like to see whether it's possible to install Ubuntu 8.10 to my desktop using a USB/flash drive.

Here are my 3 available USB options:

   1. I have a 256 MB USB dongle (everything can be erased),
   2. a 1 GB Micro SD card in my cell phone that connects via USB (everything can be erased)
   3. and a 30 GB iPod ( I have stuff on my iPod that I don't want to erase).

My computer currently has Ubuntu 8.10 Ibex from an upgrade from 8.04 but I've got some problems using it, so I thought a fresh install of 8.10 Ibex may help solve some problems.


Using IRC chatroom, I learned that:

(a) there is a 10 MB "compactCD" (a.k.a "net-install CD")  iso file that installs just the minimal offline, and then download all other packages via the internet later on ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD))

(b) it is possible to install Ubuntu 8.10 via USB drive ([https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick))

My question is: Can I do both (a) and (b) at the same time? In other words, can i put the tiny 10 MB iso file onto my 256 MB USB/flash drive/dongle/key? If so please tell me how to do so step by step. Thank you.

---

### Post by shaggy999 on 2008-10-30
You will want to look into 'unetbootin' and other utilities. They let you make a bootable usb drive from a bootable iso. With a 256 mb flash drive your only option would be the minimal CD. However, I didn't see a minimal CD release when I was grabbing isos this morning. Network support could be an issue with the minimal CD as well.

I highly recommend not trying to use your ipod as you could brick it. USB drives are so cheap nowdays. Can you not spend $10 on a 1 GB drive? Then you could use the live install CD to make the bootable key.

---

### Post by nynoah on 2008-10-30
You need atleast the 1 gig.  I am not sure if I am understanding your questions totally.  Usually USB installs are for portable desktops.  If you want to just install Ubuntu normally but without a disk and use the Flash drive as the disk, just burn a copy of the normal ISO to it that way.  Then when you boot back into your computer, reset your Bios to boot from Flash drive first and it will recognize your ISO in the flash drive.

---

### Post by Duck2006 on 2008-10-30
If you can get a 1Gb flash drive this may help.

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by hanzj on 2008-10-30
According to [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD), there is a 8.10 Ibex Minimal CD version of 9.9 MB .

---

### Post by nynoah on 2008-10-30
My understanding of the pendrive option in Ibex is that you will not longer need to go through the convoluted process described in the pendrive linux website. The new form of Ubuntu will be like Open Suse and have an option built into the installer that natively has all the necessary modifications needed to correctly install Ubuntu onto a flash drive.

---

### Post by nynoah on 2008-10-30
Also what are you trying to accomplish.  Installing to RUN on the flash drive alone (without ever installing onto computer hard drive) or just placing the ISO file on there to keep from using a CD rom burned copy?

---

### Post by hanzj on 2008-10-30
I think I see now what steps to take:

1) Go to [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
2) Save the Link to the 8.10 MinimalCD iso file (at [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-i386/current/images/netboot/mini.iso) ) onto the desktop

3) Go to [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)  
4) Download unetbootin (for ubuntu, [http://unetbootin.sourceforge.net/unetbootin-i386-latest.deb](http://unetbootin.sourceforge.net/unetbootin-i386-latest.deb) )
5) Power on the untebootin program
6) Select the radio button for "Disk Image" and select the small 10 MB iso that is saved on the desktop.
7) Proceed from there.

---

### Post by hanzj on 2008-10-30
> **nynoah said:**
> Also what are you trying to accomplish.  Installing to RUN on the flash drive alone (without ever installing onto computer hard drive) 
No. I want to install ubuntu 8.10 on computer hard drive. I want  the USB drive thing to be just a one-time thing.

> or just placing the ISO file on there to keep from using a CD rom burned copy?
Yes, I want to save my CD-Rom discs if possible.

---

### Post by nynoah on 2008-10-30
Use the 1 gig flash drive stick.  wipe it clean.  Then drop the ISO file into it without doing any type of install.  Then when you boot up into your computer, go into your BIOS settings and reset the primary boot drive to your Flash drive, your secondary boot to your hard drive.  The just install like you normally would.  If you are putting this on your normal computer I would not bother with the limited small distro install.  Go for the normal one.  It will be less hassle to you in the long run.



The other method of installing onto a flash drive is for when people want to use the flash drive alone as a portable OS to be plugged into and RUN off that flash drive alone, NEVER installing on the computer it is plugged into.

---

### Post by hanzj on 2008-10-30
My 1 GB thing is not a stick per se. IT's a 1GB Micro SD card in my cellphone that I can attach to my desktop computer via USB. Will this still work???

---

### Post by nynoah on 2008-10-30
Its really just the same as a flash drive too.  All you need is a storage medium and an ability to direct your bios to boot off that.

---

### Post by hanzj on 2008-10-30
Great. So I'll try the 1GB Cellphone SD card method first. Failing that, I'll go to the minimal cd iso on 256mb drive path.

---

### Post by Beatsake on 2008-10-31
> **nynoah said:**
> my understanding of the pendrive option in ibex is that you will not longer need to go through the convoluted process described in the pendrive linux website. The new form of ubuntu will be like open suse and have an option built into the installer that natively has all the necessary modifications needed to correctly install ubuntu onto a flash drive.

how to do this?


Never Mind Found it on another post.

boot from live CD and select:

System>Admin>Create a usb startup disk,

---

### Post by hanzj on 2008-10-31
how do i wipe clean the 1 gig flash drive? In Win XP? 
There's a file that won't get deleted?

---

### Post by hanzj on 2008-10-31
when you say "drop the ISO file", I do not just copy the iso file onto the 1GB MicroSD card, do I?

---

