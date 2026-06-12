---
title: "Built in SD card reader driver download"
date: 2015-11-13
forum: New to Ubuntu
---

### Post by matthew119 on 2015-11-13
Hey guys, I'm new to Linux. To try it out I installed Ubuntu 14.04 on an old Dell Inspiron 910 Mini with a built in SD card reader. This also goes for the USB drives on the laptop, none of them work. I can plug in an SD card or a wireless mouse dongle or a regular USB Flash Drive and none of them are registered in the computer. Any help?

---

### Post by cariboo on 2015-11-14
You should be able to see if the devices are detected when they are plugged in, by checking dmesg. Open a terminal, and right after you plug a device in type the following command:

```
dmesg
```

**Note** I'm using a usb sd card reader, as my desktop system does have a card reader slot.

The output you get should be something similar to this:

```
[91754.102465] usb 6-4: new high-speed USB device number 2 using ehci-pci
[91754.383306] usb 6-4: New USB device found, idVendor=1307, idProduct=0310
[91754.383313] usb 6-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[91754.383317] usb 6-4: Product: Mass Storage Device
[91754.383321] usb 6-4: Manufacturer: Generic
[91754.383324] usb 6-4: SerialNumber: 00000000000006
[91754.458436] usb-storage 6-4:1.0: USB Mass Storage device detected
[91754.458598] scsi host4: usb-storage 6-4:1.0
[91754.458751] usbcore: registered new interface driver usb-storage
[91754.461093] usbcore: registered new interface driver uas
[91756.154691] scsi 4:0:0:0: Direct-Access     Generic  USB  SD Reader   0.00 PQ: 0 ANSI: 2
[91756.155350] sd 4:0:0:0: Attached scsi generic sg3 type 0
[91756.156498] sd 4:0:0:0: [sdc] 7744512 512-byte logical blocks: (3.96 GB/3.69 GiB)
[91756.157121] sd 4:0:0:0: [sdc] Write Protect is off
[91756.157127] sd 4:0:0:0: [sdc] Mode Sense: 03 00 00 00
[91756.157739] sd 4:0:0:0: [sdc] No Caching mode page found
[91756.157745] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[91756.162878]  sdc: sdc1
[91756.166329] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

---

