---
title: "make USB-Stick bootable that has format ntfs"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by Jake1000 on 2012-03-19
Hello guys,
I want to make a usb stick bootbable so i can install a windows 7 iso on another computer.
This should be possible with the program Unetbootin, but the latest version doesn't support a stick formated to ntfs. The older version of Unetbootin 494 does support this, but the installation doesn't work. I think this is because it is 32-bit and I have a 64 bit machine. 
Are there any other programs I could use to make the ntfs-stick bootable or should it be possible to install the 32 bit unetbootin?

---

### Post by Mark Phelps on 2012-03-19
If you obtained this ISO file (legally) from Digital River, that site also includes instructions for using a free MS utility to do what you want.

So, why are you then having to ask these questions?

---

### Post by oklokl on 2012-03-19
[http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/)

The default usb =>fat32 no error..

fdisk -l

mkfs.vfat /dev/sdbX

or
gparted

---

### Post by dipakwaykar on 2012-03-19
Hey,
You can try universal usb installer it is available on following link, it very easy to make usb bootable,

There is no need to  format USB stick using NTFS.

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by Mark Phelps on 2012-03-20
> **dipakwaykar said:**
> Hey,
You can try universal usb installer it is available on following link, it very easy to make usb bootable,

There is no need to  format USB stick using NTFS.

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

The OP clearly stated he wanted to use the USB stick to install Windows 7.  

As stated on their website:

> Universal USB Installer is a Live Linux USB Creator that allows you to choose from a selection of Linux Distributions to put on your USB Flash Drive.

Notice the part that says "Linux Distributions" ?

---

### Post by C.S.Cameron on 2012-03-20
Using gparted, format the stick NTFS and set the boot flag.
Using Archive Manager, extract the Win 7 iso to the stick.
(or copy the DVD to the stick)
Set BIOS to use the stick as first HDD.
Boot the stick and install Win 7, (yuck).

---

### Post by Geezanansa on 2012-03-27
In this guide which was posted in recent similar thread [http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)  Thank you to mips.
In this guide explains recent and current version of unetbootin does not give ntfs option on usb.

Older versions of unetbootin do "see" ntfs partitions on usb flash drives.  So that you can burn .iso to ntfs check the link in the gude.


Still can not confirm this works yet though as i am trying to create a bootable usb with windows 8 consumer preview to install on other partition  and still no worky for me ....

Think it is recommended to make windows installers on windows sytem.

---

