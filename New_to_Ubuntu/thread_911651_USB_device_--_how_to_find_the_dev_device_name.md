---
title: "USB device -- how to find the /dev device name???"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by cwmoser on 2008-09-05
Say I plug in a USB device and it does not auto mount, what command can I issue to learn the /dev device name?

Thanks

CW

---

### Post by oldos2er on 2008-09-05
> **cwmoser said:**
> Say I plug in a USB device and it does not auto mount, what command can I issue to learn the /dev device name?

Thanks

CW

 ls /dev/usb/*

---

### Post by knix on 2008-09-05
one way is to just make a logical guess. in other words, if you have a hard drive /dev/sda, and no cd drive of that connection type, then sdb1. if you have two sata drives, then sdc1. it basically adds it as an sd_ when you plug it in, letter after everything else. 


Or, just add the disk mounter applet to the gnome panel if you use gnome:) that's the real easy way.

---

### Post by keplerspeed on 2008-09-05
the way I find out is by entering the code:

dmesg

this 'displays messages' hence the name, and will say 'device disconnected from /dev/usb* whatever it maybe. saves searching through /dev/ and guessing.

Cheers big ears

---

### Post by cwmoser on 2008-09-06
So far the only command I found that would identify the /dev name is:

sudo  fdisk  -l


Are there other commands????

Carl

---

### Post by philinux on 2008-09-06
You can look in /etc/fstab

cat /etc/fstab

However in my case I have no permanent mount point for my usb stick.

When it's plugged in it appears as USBDISK on the desktop and also in /media/ as USBDISK

---

### Post by Lusse on 2008-09-06
mount

the last line should display something like /dev/sdc1 on /media/disk type vfat (...)

//Linus

---

