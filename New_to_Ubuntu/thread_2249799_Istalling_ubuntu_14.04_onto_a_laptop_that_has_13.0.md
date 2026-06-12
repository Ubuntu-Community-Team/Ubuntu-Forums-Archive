---
title: "Istalling ubuntu 14.04 onto a laptop that has 13.04 using a usb flash drive"
date: 2014-10-24
forum: New to Ubuntu
---

### Post by olivier8 on 2014-10-24
Do I need to format the usb drive?  I selected the usb drive option from the boot menu.  It does not seem to detect the usb drive.  It just boots to the previously installed version 13.04.  If I do need to format the drive how do I format the drive in ubuntu?

---

### Post by sudodus on 2014-10-24
It depends which tool you use to make the USB boot drive. ***mkusb*** needs no formatting. ***Unetbootin*** and the ***Ubuntu Startup Disk Creator*** want a partition with  the FAT32 file system. See this link for more details

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You can use ***gparted*** to edit partitions and create file systems. If not already installed, use

```
sudo apt-get install gparted
```

---

### Post by oldrocker99 on 2014-10-24
> **sudodus said:**
> It depends which tool you use to make the USB boot drive. ***mkusb*** needs no formatting. ***Unetbootin*** and the ***Ubuntu Startup Disk Creator*** want a partition with  the FAT32 file system. See this link for more details

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You can use ***gparted*** to edit partitions and create file systems. If not already installed, use

```
sudo apt-get install gparted
```

+1 on formatting the USB to FAT; otherwise you may well get an "operating system not found" error instead of a bootable USB.

---

### Post by haplorrhine on 2014-10-24
StartUpDiskCreator wouldn't cooperate until I formatted the usb drive to fat.

I vaguely recall doing the formating with GParted... ?

---

