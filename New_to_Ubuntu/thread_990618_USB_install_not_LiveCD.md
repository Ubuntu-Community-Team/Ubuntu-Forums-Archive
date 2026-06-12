---
title: "USB install not LiveCD"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by burnetbj on 2008-11-22
Hi People

Was just messing around with the new feature in IBEX to create a USB start up disc. So I ran up and bought a 4Gb flash. Was able to create a start up disc with 8.04 LiveCD, however this is not what I am looking for. What I need is a ISO installed on the Flash like its a HDD so I can just boot from USB. 

Anyone got a link to a image I can use and a link to a tuorial to make this happen?

Thanks

---

### Post by Gannon8 on 2008-11-22
[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/#more-401](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/#more-401)

Written for 8.04, but should still work.

If you just want to have a portable system on a flash drive, then use the built-in USB installer.

---

### Post by burnetbj on 2008-11-22
Hi there

Appreciate you helping me, I have tried to use the create a USB startup disk feature 

Seems to have worked fine as it boots to the drive, but its a LiveCD this isnt what I want I actually want Ubuntu installed on a flash drive so I can just boot from USB and be up and running like the USB is my only HDD

Thanks

---

### Post by Keen101 on 2008-11-22
if you want a fully installed system on the USB drive, then just go through a normal ubuntu install, but select usb drive.

It might work best if you unplug all internal drives while doing this, but is not necessary if you be careful and tell GRUB where to install.

---

### Post by aurelieng on 2008-11-23
You can :
* unplug your disks (for safety)
* then plug your key
* put the desktop liveCD in your optical drive
* then boot, to start the installation
* Follow all the instructions normally until you reach the partitioning menu
* there, check that you are really installing on your flash drive. Add the "relatime" option to your partitions.
* Complete the installation and reboot on your USB key.
* Done :)

You might have a grub error, and if so you need to install syslinux as a bootloader instead of grub. Check around for the links on how to do it (you can use the syslinux.cfg of the liveCD as a starting point (the script isotostick.sh @ [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) is a good starting point)

At the end, you have a bootable flash drive with ubuntu. This is not an install cd or a "livecd on usb", but a real distro. If you plan to move the key from one computer to another, you need to to regenerate your /etc/X11/xorg.conf upon boot: ddd dexconf & at the end to your /etc/init.d/rc.local.

To prevent a premature wear of your USB key, you can also mount /var/tmp, /var/log, and /tmp as ramdisk. See [http://wiki.ubuntu.org.cn/UbuntuHelp:AspireOne#REDUCING_SSD_WEAR:](http://wiki.ubuntu.org.cn/UbuntuHelp:AspireOne#REDUCING_SSD_WEAR:) for more informations.

Hope this help !

---

