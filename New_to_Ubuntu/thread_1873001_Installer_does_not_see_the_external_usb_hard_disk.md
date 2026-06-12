---
title: "Installer does not see the external usb hard disk"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by And_ on 2011-10-31
I am trying to install Ubuntu 11.10 in a USB hard disk(external). I have installed the iso software in the usb hard disk and I am able to boot without any problems. 
In Ubuntu, I start the installation process and I select the "other" option but the installantion program only sees my internal harddisk (sda) where the Windows Vista is installed. It does not see that there is a usb harddisk. 
How can I get the installer to see that there is a USB Harddisk?

---

### Post by coffeecat on 2011-10-31
Hi and welcome to the forum.

Can you clarify this, please?

> **And_ said:**
> I have installed the iso software in the usb hard disk and I am able to boot without any problems.

By ISO software, I presume you mean the ISO for the Ubuntu live desktop or alternate CD. How did you install that to the USB disc? You cannot install to a partition that the live system is running from.

How big is the USB hard drive and how many partitions does it have?

---

### Post by And_ on 2011-10-31
> **coffeecat said:**
> Hi and welcome to the forum.
 
Can you clarify this, please?
 
 
 
By ISO software, I presume you mean the ISO for the Ubuntu live desktop or alternate CD. How did you install that to the USB disc? You cannot install to a partition that the live system is running from.
 
How big is the USB hard drive and how many partitions does it have?
 
I used the software Universal-USB-installer1.8.6.4.exe  to create a "USB stick" with the ISO for the Ubuntu. THe USB stick is actually a hard disk with a capacity of 500 G
The only data in the usb disk is the boot software. There must be only one partition. I was expecting to create the other partitions during the installation...

---

### Post by coffeecat on 2011-10-31
I don't have experience of that piece of software but it's possible that's not going to work. Because the various apps for making a bootable pendrive from a Linux ISO expect a - well - pendrive, they tend to make one partition covering the whole of the drive. It could be that you've got a huge 500GB partition with the live USB files taking up only about 700MB.

I suggest you write the ISO to a real pendrive and use that to boot up and partition and install to your 500GB USB drive. If you do, be very careful where grub (the bootloader) is installed. Make sure you install grub to the mbr of the USB drive and not to the mbr of the internal HD of your machine otherwise your machine will only be able to boot with the external HD attached. 

I'm sure the Windows exe you found is perfectly good, but a Windows USB writing app is included in the Ubuntu ISO. Have a look here:

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

And:

[https://help.ubuntu.com/community/Installation/FromUSBStick#From_Windows](https://help.ubuntu.com/community/Installation/FromUSBStick#From_Windows)

---

### Post by spiky001 on 2011-10-31
It is best to remove your 1st disk before installing to 2nd disk, just incase something gose wrong.  If you cant  Burn the iso img to cd/usb pendrive then boot off the cd/usb pendrive then select install when you get to the part where to install if you select manual install it will ask where you want to install it to i,e sdb  Have a read through [here]("http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/")

---

### Post by ixtok on 2011-10-31
I don't think you can install ubuntu the way you are trying to do it. Depending on your computer, you should either make a live cd or the equivalent of live cd on a separate memory stick. You can then boot the computer with that and then install into your external usb hard drive. I don't think you can install to the medium you are booting from.

---

