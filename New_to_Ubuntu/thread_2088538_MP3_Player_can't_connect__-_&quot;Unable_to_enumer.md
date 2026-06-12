---
title: "MP3 Player can't connect  - &quot;Unable to enumerate USB device on port x&quot;"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by salemjohn on 2012-11-26
I have a SanDisk Sansa Clip Zip mp3 player. When I plug it in to the USB port, I get the following:

$ dmesg
...
usb 1-3: new high-speed USB device number 11 using ehci_hcd
hub 1-0:1.0: unable to enumerate USB device on port 3

The Sansa does not show up in lsusb, or in fdisk.

I believe it is not a problem with the cable or the player, as a test-run on a Mac worked fine. Beyond this, I can't really figure out what's going on. Does anyone know how I might troubleshoot this further? Many thanks.

Running Ubuntu 12.04, kernel is "3.2.0-33-generic." The Sansa Clip Zip has the latest firmware.

---

