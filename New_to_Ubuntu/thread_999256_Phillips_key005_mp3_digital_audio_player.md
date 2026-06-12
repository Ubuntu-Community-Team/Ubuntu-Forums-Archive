---
title: "Phillips key005 mp3 digital audio player"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by DesiArnez6 on 2008-12-01
I just received the Phillips key005 digital audio player (mp3 player) in the mail as a Holiday gift from family.

 I am not sure if this is Ubuntu compatible. (I also have a computer with Windows 2000 that is rarely used just in case)

Will this work?

When I plug it in to the USB port, nothing happens at all...nothing! :)

(I run Ubuntu 7.10 Gutsy)

How can I find out whats happening? Do I need type anything into the terminal? Find the Chipset or something?

---

### Post by jgoguen on 2008-12-01
Can you provide some dmesg output?  Unplug the device, open a Terminal (Applications -> Accessories -> Terminal), plug in your device, wait 10 seconds, and enter this command:
```
dmesg | tail -n 50
```
Post the output here, hopefully it'll be helpful.

---

### Post by DesiArnez6 on 2008-12-01
Just realized, I typed it a bit wrong its Philips key005/17 (Philips with only one "l")

Anyways, I typed what you said in th terminal. This is what I got:

guestadmin@ubuntu:~$ dmesg | tail -n 50
[27455.160000] sd 8:0:0:0: rejecting I/O to offline device
[27455.160000] sd 8:0:0:0: rejecting I/O to offline device
[27455.160000] sd 8:0:0:0: rejecting I/O to offline device
[27455.160000] sd 8:0:0:0: rejecting I/O to offline device
[27455.160000] sd 8:0:0:0: rejecting I/O to offline device
[27455.160000] sd 8:0:0:0: rejecting I/O to offline device
[27455.160000] sd 8:0:0:0: rejecting I/O to offline device
[27455.160000] sd 8:0:0:0: rejecting I/O to offline device
[27455.160000] sd 8:0:0:0: rejecting I/O to offline device
[27455.160000] sd 8:0:0:0: rejecting I/O to offline device
[27455.164000] sd 8:0:0:0: rejecting I/O to offline device
[27455.164000] sd 8:0:0:0: rejecting I/O to offline device
[27455.164000] sd 8:0:0:0: rejecting I/O to offline device
[27455.164000] sd 8:0:0:0: rejecting I/O to offline device
[27455.164000] sd 8:0:0:0: rejecting I/O to offline device
[27455.164000] sd 8:0:0:0: rejecting I/O to offline device
[27455.164000] sd 8:0:0:0: rejecting I/O to offline device
[27455.164000] sd 8:0:0:0: rejecting I/O to offline device
[27455.164000] sd 8:0:0:0: rejecting I/O to offline device
[27455.164000] sd 8:0:0:0: rejecting I/O to offline device
[27455.164000] sd 8:0:0:0: rejecting I/O to offline device
[27455.172000] usb 2-2: USB disconnect, address 7
[27455.296000] usb 2-2: new full speed USB device using uhci_hcd and address 8
[27455.420000] usb 2-2: device descriptor read/64, error -71
[27455.644000] usb 2-2: device descriptor read/64, error -71
[27455.860000] usb 2-2: new full speed USB device using uhci_hcd and address 9
[27455.980000] usb 2-2: device descriptor read/64, error -71
[27456.204000] usb 2-2: device descriptor read/64, error -71
[27456.420000] usb 2-2: new full speed USB device using uhci_hcd and address 10
[27456.828000] usb 2-2: device not accepting address 10, error -71
[27456.940000] usb 2-2: new full speed USB device using uhci_hcd and address 11
[27457.348000] usb 2-2: device not accepting address 11, error -71
[27567.756000] ata1.01: qc timeout (cmd 0xa0)
[27567.756000] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[27567.756000] ata1.01: cmd a0/00:00:00:00:20/00:00:00:00:00/b0 tag 0 cdb 0x25 data 8 in
[27567.756000]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[27572.796000] ata1: port is slow to respond, please be patient (Status 0xd1)
[27577.780000] ata1: device not ready (errno=-16), forcing hardreset
[27577.780000] ata1: soft resetting port
[27578.140000] ata1.00: configured for UDMA/100
[27578.328000] ata1.01: configured for UDMA/25
[27578.328000] ata1: EH complete
[27578.344000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[27578.352000] sd 0:0:0:0: [sda] Write Protect is off
[27578.352000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[27578.368000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[27578.392000] sd 0:0:0:0: [sda] 195371568 512-byte hardware sectors (100030 MB)
[27578.400000] sd 0:0:0:0: [sda] Write Protect is off
[27578.400000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[27578.416000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

---

### Post by jgoguen on 2008-12-01
Doesn't look good.  Maybe someone else knows how to get it working.  My Google-fu is weak tonight :(  Unless there's some reason you can't upgrade, I would recommend updating to 8.04 and trying again, then upgrading to 8.10 if it still won't work.  Make sure you make backups of your important data first!

---

### Post by DesiArnez6 on 2009-01-12
I gave up. I couldn't get it working in Ubuntu, so I do not recommend this mp3 plyer for Ubuntu as it will not work.

I resorted to the following: Moving my music from Ubuntu laptop with a flash drive, over to my Windows 2000 desktop, and then using windows to transfer the music to the mp3 player ;)

---

