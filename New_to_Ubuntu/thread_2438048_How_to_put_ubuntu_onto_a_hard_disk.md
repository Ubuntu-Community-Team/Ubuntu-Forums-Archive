---
title: "How to put ubuntu onto a hard disk"
date: 2020-03-04
forum: New to Ubuntu
---

### Post by xxxdakevingame on 2020-03-04
I have this new hard disk for my old vaio laptop which currently has no operating system. I want to put ubuntu onto the hard disk and use it to boot ubuntu and to install it. Kinda like when you put ubuntu onto a usb to boot off of.

---

### Post by Skaperen on 2020-03-04
can you describe the _system_ that hard drive *is* or *will be* attached to?  i am especially interested in knowing if there is a *bootable* USB (version 2 pr version 3), camera memory card slot, CD reader, or DVD reader.

---

### Post by Impavidus on 2020-03-05
The easiest way is to simply put the hard drive in the laptop, create a live disk (usb, dvd, maybe something else) and use that to install Ubuntu. If you can't (maybe it's too old to boot from usb and the dvd drive is broken), the best option would be to put the hard drive in a different computer (or attach it by usb), create a live disk, install Ubuntu on the new hard drive, then transfer the hard drive (with Ubuntu already installed) to the old laptop. Make sure that you don't install any proprietary drivers and that you install in the right mode (UEFI or legacy).

---

### Post by C.S.Cameron on 2020-03-05
You can use balenaEtcher to put Ubuntu Live installer on a hard disk.
Open Etcher.
Click the settings icon on the upper right, a new screen will open.
Select Unsafe mode on the bottom, 
Click Enable unsafe mode
Click back.
Select image
Click select target
Pick your target hard drive.
Select Flash.
All data on it will be overwritten.

Edit:
If you boot toram and unmount the HDD after booting, you can install Full Ubuntu directly to it.
If you have a flash drive it is probably easier to put Ubuntu on that and install the old fashion way.

---

### Post by yancek on 2020-03-05
> I want to put ubuntu onto the hard disk and use it to boot ubuntu and to  install it. 

Definitely possible but you don't provide enough details for anyone to give info.  Do you have an OS with a proper bootloader currently installed to boot the Ubuntu iso?  If not, you can put  Ubuntu on the hard drive in the same fashion in which you put it on a usb.  In order to then install to that same drive, you will need another Linux OS to shrink the Ubuntu iso files partition to leave room on which you can install Ubuntu

> Kinda like when you put ubuntu onto a usb to boot off of. 

Not really the same thing as installing from a usb to a hard drive.  What you seem to want is to boot from a hard drive (with or without an OS?) and install to the same hard drive. You might do an online search for installing Ubuntu with toram option.

---

### Post by TheFu on 2020-03-05
> **xxxdakevingame said:**
> I have this new hard disk for my old vaio laptop which currently has no operating system. I want to put ubuntu onto the hard disk and use it to boot ubuntu and to install it. Kinda like when you put ubuntu onto a usb to boot off of.

You cannot both boot and install to the same storage device.  Experts can. I've never tried because there are 50 easier methods.

You can put an image onto almost any bootable media.  Flash media is the most commonly used, since most machines have an SDcard slot, CF or SONY-MS or USB port.  Then just tell the computer BIOS to boot from that device and install to the other connected storage. May need to use the "do something else" option to install to non-internal storage.

Not to over think this: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Windows: [https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-windows)
Ubuntu: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu)
OSX: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos)

---

### Post by C.S.Cameron on 2020-03-05
> **TheFu said:**
> You cannot both boot and install to the same storage device.

Installing Ubuntu to the drive the Live installer was booted from is just a matter of booting toram and then unmounting the boot drive.
The boot drive is then writable and the installer is running in RAM. You do need more RAM than the size of the ISO.

See [https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from](https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from)

---

### Post by TheFu on 2020-03-05
> **C.S.Cameron said:**
> Installing Ubuntu to the drive the Live installer was booted from is just a matter of booting toram and then unmounting the boot drive.
The boot drive is then writable and the installer is running in RAM. You do need more RAM than the size of the ISO.

See [https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from](https://askubuntu.com/questions/855039/can-ubuntu-be-installed-to-the-pendrive-it-was-booted-from)

That's just crazy, but if Sudodus did it, I believe it.  There are so many great uses for a *Try Ubuntu* flash drive to perform system maintenance, it is worth having at least one Flash drive/SDHC setup just for that.  But we don't have all the info about the situation. Perhaps there isn't any other choice?

---

### Post by C.S.Cameron on 2020-03-05
@TheFu

I recall the original Op only had one flash drive and wanted a Full install.

It is also possible to make a mkusb persistent install to a Live only flash drive using similar method.

[https://askubuntu.com/questions/855696/can-a-persistent-ubuntu-install-be-made-to-the-pendrive-it-was-booted-from](https://askubuntu.com/questions/855696/can-a-persistent-ubuntu-install-be-made-to-the-pendrive-it-was-booted-from)

---

