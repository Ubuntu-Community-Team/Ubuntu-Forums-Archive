---
title: "USB Tablet no longer mounts to my Ubuntu ..."
date: 2015-01-12
forum: New to Ubuntu
---

### Post by cwmoser on 2015-01-12
Cannot any longer mount my Samsung Tablet via USB Cable.
Using MTP, Ubuntu 14.04.
Tablet beeps on plugging in Cable but no mount points

dmesg shows:
```

[ 1442.032246] usb 1-4.4.1: new high-speed USB device number 13 using ehci-pci
[ 1442.126158] usb 1-4.4.1: New USB device found, idVendor=04e8, idProduct=6860
[ 1442.126164] usb 1-4.4.1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 1442.126166] usb 1-4.4.1: Product: SAMSUNG_Android
[ 1442.126167] usb 1-4.4.1: Manufacturer: SAMSUNG
[ 1442.126169] usb 1-4.4.1: SerialNumber: 30046423708b9100
[ 1563.465065] usb 1-4.4.1: USB disconnect, device number 13
[ 1585.416277] usb 1-4.4.1: new high-speed USB device number 14 using ehci-pci
[ 1585.509788] usb 1-4.4.1: New USB device found, idVendor=04e8, idProduct=6860
[ 1585.509791] usb 1-4.4.1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 1585.509792] usb 1-4.4.1: Product: SAMSUNG_Android
[ 1585.509794] usb 1-4.4.1: Manufacturer: SAMSUNG
[ 1585.509796] usb 1-4.4.1: SerialNumber: 30046423708b9100


```

---

### Post by cwmoser on 2015-01-12
I need to understand how to debug MTP.  All an archane thing.

---

### Post by ajgreeny on 2015-01-12
Have you seen the thread at [http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702) and tried to use the info there?  It worked straight away for my Acer tablet.

---

### Post by cwmoser on 2015-01-12
Went throught that thread, tried the editing of the files.  Still not working.
Wondering if a system update is the cause.

---

### Post by cwmoser on 2015-01-12
Got my Android Tablet to connect to Ubuntu intermitently this way:

From a terminal window:

Mount:
mkdir ~/mtp
jmtpfs ~/mtp
ls ~/mtp

Unmount:
fusermount -u ~/mtp

Its a rinky dink solution that does not work reliably.

Found the above solution here:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1314556](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/1314556)

---

