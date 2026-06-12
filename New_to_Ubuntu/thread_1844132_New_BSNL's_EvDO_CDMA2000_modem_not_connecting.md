---
title: "New BSNL's EvDO CDMA2000 modem not connecting"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by eshant_engineer on 2011-09-14
Hi,

I have gone through ndiswrapper method, but didn't found .inf driver to load. Now what I have tried is through network manager, but no success.

on connecting it is showing as 1 removable mass storage and 1 removable cd drive in Disk utility.

I am attaching logs, please see what is wrong and what can be done in this issue. Since it is detectable so I assume that there is some solution to get my wireless dongle working.

PS: I know wvdial method but it bypass any layer due to which chat, gwibber and other services don't connect,


dmesg:-
```

[   77.035363] usb 2-1.2: new full speed USB device using ehci_hcd and address 4
[   77.115279] usb 2-1.2: device descriptor read/64, error -32
[   77.338053] scsi7 : usb-storage 2-1.2:1.0
[   78.336986] scsi 7:0:0:0: CD-ROM            BSNL     Mass Storage CD  7.00 PQ: 0 ANSI: 2
[   78.342399] sr1: scsi-1 drive
[   78.342705] sr 7:0:0:0: Attached scsi CD-ROM sr1
[   78.343026] sr 7:0:0:0: Attached scsi generic sg3 type 5
[   78.376053] usb 2-1.2: USB disconnect, address 4
[   78.685196] usb 2-1.2: new full speed USB device using ehci_hcd and address 5
[   78.797291] usbserial_generic 2-1.2:1.0: generic converter detected
[   78.797514] usb 2-1.2: generic converter now attached to ttyUSB0
[   78.797965] usbserial_generic 2-1.2:1.1: generic converter detected
[   78.798157] usb 2-1.2: generic converter now attached to ttyUSB1
[   82.433256] usb 2-1.2: USB disconnect, address 5
[   82.433647] generic ttyUSB0: generic converter now disconnected from ttyUSB0
[   82.433688] usbserial_generic 2-1.2:1.0: device disconnected
[   82.434112] generic ttyUSB1: generic converter now disconnected from ttyUSB1
[   82.434152] usbserial_generic 2-1.2:1.1: device disconnected
[   84.205090] usb 2-1.2: new full speed USB device using ehci_hcd and address 6
[   84.284985] usb 2-1.2: device descriptor read/64, error -32
[   84.508527] usbserial_generic 2-1.2:1.0: Generic device with no bulk out, not allowed.
[   84.508536] usbserial_generic: probe of 2-1.2:1.0 failed with error -5
[   84.508546] cdc_acm 2-1.2:1.0: This device cannot do calls on its own. It is not a modem.
[   84.508575] cdc_acm 2-1.2:1.0: ttyACM1: USB ACM device
[   84.509585] scsi8 : usb-storage 2-1.2:1.2
[   85.506856] scsi 8:0:0:0: CD-ROM            BSNL     Mass Storage CD  7.00 PQ: 0 ANSI: 2
[   85.507836] scsi 8:0:0:1: Direct-Access     BSNL     Mass Storage SD  7.00 PQ: 0 ANSI: 0 CCS
[   85.512100] sr1: scsi-1 drive
[   85.512621] sr 8:0:0:0: Attached scsi CD-ROM sr1
[   85.514533] sr 8:0:0:0: Attached scsi generic sg3 type 5
[   85.515250] sd 8:0:0:1: Attached scsi generic sg4 type 0
[   85.528114] sd 8:0:0:1: [sdc] Attached SCSI removable disk
```

Thanks in advance..

---

### Post by LowSky on 2011-09-14
can you past your results to lsusb, what you included isn't the correct output, it should like similar to this:

```


$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 004 Device 003: ID 2040:4902 Hauppauge HD PVR
Bus 005 Device 003: ID 090c:6000 Silicon Motion, Inc. - Taiwan (formerly Feiya Technology Corp.) SD/SDHC Card Reader (SG365 / FlexiDrive XC+)
Bus 006 Device 002: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 007 Device 002: ID 1997:0409  
Bus 007 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 009 Device 002: ID 046d:c068 Logitech, Inc. G500 Laser Mouse
Bus 001 Device 004: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 001 Device 005: ID 0609:0334 SMK Manufacturing, Inc. eHome Infrared Receiver
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. Mouse (Boot Interface Subclass)
Bus 007 Device 006: ID 0a5c:2148 Broadcom Corp. BCM92046DG-CL1ROM Bluetooth 2.1 Adapter
Bus 001 Device 006: ID 0781:74d1 SanDisk Corp. Sansa Clip+ (msc)
Bus 001 Device 007: ID 03f0:4117 Hewlett-Packard LaserJet 1018

```

---

### Post by eshant_engineer on 2011-09-16
oh sorry, here is lsusb:


```
Bus 003 Device 002: ID 046d:c05a Logitech, Inc. Optical Mouse M90
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 006: ID 15eb:1231  ***//this is my modem***
Bus 002 Device 004: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1bcf:2881 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 8086:0189 Intel Corp. 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by eshant_engineer on 2011-09-17
please somebody help on this issue, and also please let me know how to request Ubuntu organization to include support for my device in future releases.

---

### Post by eshant_engineer on 2011-09-18
bump..

---

### Post by dineshs on 2011-09-19
> PS: I know wvdial method but it bypass any layer due to which chat, gwibber and other services don't connect,Did you try wvdial ?
[http://abhishek.nagar.me/blogs/configuring-bsnl-evdo-modem-debian-gnulinux](http://abhishek.nagar.me/blogs/configuring-bsnl-evdo-modem-debian-gnulinux)

---

### Post by eshant_engineer on 2011-09-19
> **dineshs said:**
> Did you try wvdial ?
[http://abhishek.nagar.me/blogs/configuring-bsnl-evdo-modem-debian-gnulinux](http://abhishek.nagar.me/blogs/configuring-bsnl-evdo-modem-debian-gnulinux)

Yes I know it works. But I don't want to sacrifice important background services when I know, if any Ubuntu guru support, I can get this working from Network Manager itself.

 This is not ZTE made modem. There was no issue in connecting through ZTE modem(I had earlier). But the new modem is made by  BSNL itself whose name given is "Prithvi" which ubuntu detects but can't connect(I have given relevant log for the same). 

This device is detected as modem, mass storage media and CD-ROM.

---

