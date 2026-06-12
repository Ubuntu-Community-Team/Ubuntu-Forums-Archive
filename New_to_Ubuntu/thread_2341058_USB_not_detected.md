---
title: "USB not detected"
date: 2016-10-24
forum: New to Ubuntu
---

### Post by rockernaxo on 2016-10-24
Hi!

My USB isn't recognized anymore by Ubuntu. I've tried to format it, but it does not show on fdisk.

Here is the info:
```

~$ lsusb
Bus 002 Device 004: ID 5986:0292 Acer, Inc 
Bus 002 Device 009: ID abcd:1234 Unknown 
Bus 002 Device 010: ID 15d9:0a4c Trust International B.V. USB+PS/2 Optical Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Now it shows as unknown.

```
:~$ dmesg | tail -n 20
[ 1293.517767] scsi host4: usb-storage 2-1.2:1.0
[ 1293.517855] scsi host4: runtime PM trying to activate child device host4 but parent (2-1.2:1.0) is not active
[ 1309.075696] usb 2-1.2: USB disconnect, device number 8
[ 1326.465920] usb 2-1.1: USB disconnect, device number 3
[ 1379.856921] usb 2-1.2: new high-speed USB device number 9 using ehci-pci
[ 1379.966250] usb 2-1.2: New USB device found, idVendor=abcd, idProduct=1234
[ 1379.966257] usb 2-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1379.966261] usb 2-1.2: Product: UDisk           
[ 1379.966265] usb 2-1.2: Manufacturer: General 
[ 1379.966268] usb 2-1.2: SerialNumber: 1310152237165113404613
[ 1379.967233] usb-storage 2-1.2:1.0: USB Mass Storage device detected
[ 1379.967468] scsi host4: usb-storage 2-1.2:1.0
[ 1379.967612] scsi host4: runtime PM trying to activate child device host4 but parent (2-1.2:1.0) is not active
[ 1402.648424] usb 2-1.2: reset high-speed USB device number 9 using ehci-pci
[ 2166.114044] usb 2-1.1: new low-speed USB device number 10 using ehci-pci
[ 2166.226968] usb 2-1.1: New USB device found, idVendor=15d9, idProduct=0a4c
[ 2166.226975] usb 2-1.1: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[ 2166.226978] usb 2-1.1: Product:  USB OPTICAL MOUSE
[ 2166.230380] input:  USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/0003:15D9:0A4C.0002/input/input14
[ 2166.290409] hid-generic 0003:15D9:0A4C.0002: input,hidraw0: USB HID v1.11 Mouse [ USB OPTICAL MOUSE] on usb-0000:00:1d.0-1.1/input0


```

---

### Post by tuese on 2016-10-28
Install GParted
```
sudo apt-get install gparted
```
Run it and select your USB drive.
Then select "Device" - "Create Partition Table" - create "msdos".

---

### Post by leunam12 on 2016-10-28
If he only does that he is going to end up with a USB stick without a filesystem, he has to create and format a FAT32 partition after that.

---

### Post by rockernaxo on 2016-10-30
> **tuese said:**
> Install GParted
```
sudo apt-get install gparted
```
Run it and select your USB drive.
Then select "Device" - "Create Partition Table" - create "msdos".

It does not appear listed in Gparted.

---

### Post by rockernaxo on 2016-10-30
> **leunam12 said:**
> If he only does that he is going to end up with a USB stick without a filesystem, he has to create and format a FAT32 partition after that.

How should I do that? Gparted does not recognize the stick.

---

### Post by leunam12 on 2016-10-31
Does it show on a different computer? Do other USB sticks show? Maybe you have a bad stick. What do you get if you plug it in and type lsblk on the terminal?

---

