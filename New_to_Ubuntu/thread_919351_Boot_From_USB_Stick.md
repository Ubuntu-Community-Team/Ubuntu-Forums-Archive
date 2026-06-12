---
title: "Boot From USB Stick"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by mengd2002 on 2008-09-13
When installing Ubuntu, is there a way to have it boot from a USB stick?  I don't want to install it on a USB stick, just boot from it.  Thanks

---

### Post by k33bz on 2008-09-13
Im not sure I know what you mean by that?

---

### Post by phidia on 2008-09-13
I have to agree with k33bz. What is it exactly that you are trying to do?
If you use the usb drive to boot from you will need to install, at minimum, the boot directory on that drive. You will also need to setup bios to boot from usb 1st in boot order and follow the guide in the [install wiki]("https://help.ubuntu.com/community/Installation#Other%20installation%20guides").

---

### Post by Chronix33 on 2008-09-13
If your BIOS allows for it, you might be able to install a Live version of Ubuntu on your jump drive then set to boot from removable in your BIOS. I have no clue whatsoever if it will work though.

---

### Post by mengd2002 on 2008-09-13
Instead of booting from the MBR of the hard drive, I want to boot from the USB stick.

---

### Post by k33bz on 2008-09-13
Then you would have to install onto the USB drive.

Unless what you are asking to do is making a constant (i think that is the word) Live cd. Where it boots from your DVD/CD, and is able to save everything you do to a different media source, such as a USB.

Is that what you are referring to?

---

### Post by Gannon8 on 2008-09-13
[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/#more-401](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/#more-401)

Some instructions on how to do this.

---

### Post by Sirhanz on 2008-09-14
I don't think that is what he is looking for, I think you wan't to secure your system so that without the usb drive they can not boot into your system without some linuxery. If thats the case, you can install grub onto the usb/pendrive which will need some configuring to properly find your boot scripts home directory and in that case mount the hard drive. After you set up grub on the usb device, you can uninstall the bootloader on the physical hard drive installed in the system, so you would therefore need your pendrive or similar usb device with grub, properly configured to boot your system.

---

### Post by dRock1286 on 2008-09-14
> **k33bz said:**
> Then you would have to install onto the USB drive.

Unless what you are asking to do is making a constant (i think that is the word) Live cd. Where it boots from your DVD/CD, and is able to save everything you do to a different media source, such as a USB.

Is that what you are referring to?

persistent is the word actually.  :D

---

### Post by dRock1286 on 2008-09-14
> **Sirhanz said:**
> I don't think that is what he is looking for, I think you wan't to secure your system so that without the usb drive they can not boot into your system without some linuxery. If thats the case, you can install grub onto the usb/pendrive which will need some configuring to properly find your boot scripts home directory and in that case mount the hard drive. After you set up grub on the usb device, you can uninstall the bootloader on the physical hard drive installed in the system, so you would therefore need your pendrive or similar usb device with grub, properly configured to boot your system.

That will suck when the thumbdrive goes bad.........:lolflag:

---

### Post by C.S.Cameron on 2008-09-14
I am running ubuntu from thumbdrive.
by modifying grub and switchconf I am able to boot to other drives and multiple xorg.conf,s.
I don,t think it is necessary to have the full operating system on the stick, just grub should work.

---

### Post by admiralcrom on 2008-10-10
I think mengd2002 means that he has, like me, an installed system containing windows on first partition and ubuntu (kubuntu for me) on the second. And he wants to be able to install grub to boot from his usb stick into his ubuntu partition. 

I know how to do this when setting up a new install (as follows):

Have to have usb stick connected at this time.
Using a Live CD boot with it select the install option.
When you have selected the partition that you want to install the system in and get to the Advanced option click it to change the option from (hd0) to (hd1). This will put a bootloader in the MBR of the usb stick that points to the rest of the ubuntu installed partition and boots it.

Funny thing is thats ALL thats on your usb stick. So, as long as you dont partition the stick, it can be used to boot to the ubuntu install.

Problem I am having is to replicate this without reinstalling a system onto my harddrive just to do it. (IE I need to make a backup one just in case).

From what I have read and noticed (correct me if I am wrong) the reason it works is that the bootloader looks for the grub files on all harddrives. So if you have multi installations of linux it will find the first and show you it's menu.lst file for booting. So if your second install is not in that menu.lst (IE you edited it to include it) then you will never be able to boot to the second install.

Admiralcrom

P.S. I have been a winblows user for too long and got a linux bible to help me, but it's only been a few days....:-D:

---

### Post by Keen101 on 2008-10-10
> Instead of booting from the MBR of the hard drive, I want to boot from the USB stick.

You could copy the /boot/grub/ folder to your USB drive, and use the SUPER GRUB DISK to install the GRUB bootloader onto the USB drive, but i have no idea why you would want to. You would still have to edit the /boot/grub/menu.lst to boot it correctly though.

---

### Post by adrian15 on 2008-10-13
> **Keen101 said:**
> You could copy the /boot/grub/ folder to your USB drive, and use the SUPER GRUB DISK to install the GRUB bootloader onto the USB drive, but i have no idea why you would want to. You would still have to edit the /boot/grub/menu.lst to boot it correctly though.

If you install [SGD's own grub to the pendrive](http://www.supergrubdisk.org/wiki/SGD_Howto_make#How_to_make_a_Super_Grub_Disk_USB.) you can use its [usbshift command](http://www.supergrubdisk.org/wiki/SGD_usbshift) and avoid having to edit your menu.lst each time there is a kernel update.

Just edit your pendrive's menu.lst to configfile the internal hard disk menu.lst

```

default 0
timeout 0
title my linux
configfile (hd0,2)/boot/grub/menu.lst

```

Where we suppose that your linux partition partition is hda3 or sda3.

adrian15

---

