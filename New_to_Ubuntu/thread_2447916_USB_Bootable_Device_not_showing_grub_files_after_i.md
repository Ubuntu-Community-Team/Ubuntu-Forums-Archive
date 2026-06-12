---
title: "USB Bootable Device not showing grub files after installing on terminal"
date: 2020-07-28
forum: New to Ubuntu
---

### Post by micodacillo123 on 2020-07-28
can someone please help me, it is because i use my USB as a windows BOOTABLE USB, and im doing it in my ubuntu 20.04. the problem is the time when the files of the image have been copy to my documents to my USB, i use this command :
sudo grub-install --target=i386-pc --boot-directory="/media/<username>/<drive_label>/boot" /dev/sdX

when the command on terminal has finished, then checked the boot folder, every time i check the grub folder it is empty even the terminal command
 said it has no error. without those files on grub folder on boot folder, i can't use my USB as a bootable device on linux, can somebody help me 
with this problem?[SIZE=3][SIZE=4][SIZE=3][/SIZE][/SIZE][/SIZE]

---

### Post by pbear42 on 2020-07-28
What are you calling "the grub folder"?  Do you mean /boot/grub or /etc/grub.d?
Is this a live ISO drive or full install?  What method did you use to burn/install?
Are you trying to boot in BIOS or UEFI?
Are two computers involved?  If so, are they both BIOS, both UEFI, or one of each?

---

### Post by micodacillo123 on 2020-07-29
yes it is the /boot/grub or /etc/grub.d and the ISO i use is windows 8.1. i only open the ISO file whit disk image mounter and copy the files through the USB. i don't know if its BIOS or UEFI And i only have one computer

---

### Post by sudodus on 2020-07-29
In Ubuntu 20.04 LTS you can use [mkusb](https://help.ubuntu.com/community/mkusb) to create a Windows installer in your USB drive.

Install mkusb into your Ubuntu system with the following commands

```

sudo add-apt-repository universe  # only for standard Ubuntu live

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt update
sudo apt install mkusb usb-pack-efi

```

and it should be rather straight-forward to create a Windows installer via menus in mkusb.

---

### Post by pbear42 on 2020-07-29
> **micodacillo123 said:**
> ... the ISO i use is windows 8.1. i only open the ISO file whit disk image mounter and copy the files through the USB. 
If you're trying to burn a Windows ISO to flash drive, you don't use *grub-install*.  I've had success using the method described at [TechSpot]("https://www.techspot.com/guides/1721-clone-backup-usb-drive/"), but only tested with Win10.  Hadn't heard previously that mkUSB works for this, but take sudodus' word for it, as he's the developer.

---

### Post by C.S.Cameron on 2020-07-29
mkusb +1
mkusb-plug also works great for Windows installer. 
**sudo apt install mkusb-plug**
It has extra safeguards against installing to the wrong drive.

---

