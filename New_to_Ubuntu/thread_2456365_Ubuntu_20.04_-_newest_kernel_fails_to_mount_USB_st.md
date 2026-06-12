---
title: "Ubuntu 20.04 - newest kernel fails to mount USB stick"
date: 2021-01-10
forum: New to Ubuntu
---

### Post by josuegomes-gmail on 2021-01-10
I'm trying to insert an USB stick (which is also a GSM modem). The stick filesystem is ISO 9660.


With 5.4.0-42 the USB mounts correctly (excerpt):

```
[  +0.819423] usb 1-3: new high-speed USB device number 8 using xhci_hcd
[  +0.152015] usb 1-3: New USB device found, idVendor=19d2, idProduct=1589, bcdDevice= 0.00
[  +0.000005] usb 1-3: New USB device strings: Mfr=10, Product=11, SerialNumber=13
[  +0.000003] usb 1-3: Product: ZTE Mobile Broadband Station
[  +0.000002] usb 1-3: Manufacturer: ZTE,Incorporated
[  +0.000002] usb 1-3: SerialNumber: 1234567890ABCDEF
[  +0.008230] usb-storage 1-3:1.6: USB Mass Storage device detected
[  +0.025207] sr 4:0:0:0: Attached scsi CD-ROM sr0
[  +0.000192] sr 4:0:0:0: Attached scsi generic sg3 type 5
[  +0.000262] sd 4:0:0:1: Attached scsi generic sg4 type 0
[ +36.807904] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[  +0.823282] ISO 9660 Extensions: Microsoft Joliet Level 1
[  +0.010197] ISOFS: changing to secondary root
```


With 5.8.0-36


```
[  +0,815449] usb 1-3: new high-speed USB device number 8 using xhci_hcd
[  +0,151868] usb 1-3: New USB device found, idVendor=19d2, idProduct=1589, bcdDevice= 0.00
[  +0,000005] usb 1-3: New USB device strings: Mfr=10, Product=11, SerialNumber=13
[  +0,000004] usb 1-3: Product: ZTE Mobile Broadband Station
[  +0,000003] usb 1-3: Manufacturer: ZTE,Incorporated
[  +0,000002] usb 1-3: SerialNumber: 1234567890ABCDEF
[  +0,007897] usb-storage 1-3:1.6: USB Mass Storage device detected
[  +0,024179] sr 4:0:0:0: Attached scsi CD-ROM sr0
[  +0,000159] sr 4:0:0:0: Attached scsi generic sg4 type 5
[  +0,000247] sd 4:0:0:1: Attached scsi generic sg5 type 0
[jan 9 19:29] usb 1-3: USB disconnect, device number 10
```

Full traces attached.

Edit - Jan 11, 2021

5.8 syslog shows this:

```
Jan 11 07:58:54 ubuntu-dev usb_modeswitch_dispatcher[2915]: Unable to open bind list file: No such file or directory
Jan 11 07:58:54 ubuntu-dev usb_modeswitch[2915]: usb_modeswitch: add device ID 19d2:1589 to driver option
Jan 11 07:58:54 ubuntu-dev usb_modeswitch[2915]: usb_modeswitch: please report the device ID to the Linux USB developers!
```

Any idea?

syslog attached.

---

