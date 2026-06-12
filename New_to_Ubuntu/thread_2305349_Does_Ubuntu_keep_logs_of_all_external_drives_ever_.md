---
title: "Does Ubuntu keep logs of all external drives ever connected (like Windows does)?"
date: 2015-12-05
forum: New to Ubuntu
---

### Post by tom214 on 2015-12-05
I'm wondering if Ubuntu 14.04 stores identifying information about all USB drives that have ever been connected? And if so, is there any tool available to remove that information after a drive has been disconnected?

I know Windows stores such info in several registry entries and system activity logs.

---

### Post by veddox on 2015-12-05
I don't know of any programs/statistics specifically on USB drives (which doesn't mean there aren't any, though...)

What I do know is that Linux stores its logs in /var/log, if you grep for "usb" or some such in there I'm sure you'll find a lot of information.

Edit: Just noticed this is in the New to Ubuntu forum, so a small clarification: "grep" is a GNU utility for searching through text files, for more information, use the command "man grep".

---

### Post by tom214 on 2015-12-05
Thanks,

Interesting. I just ran grep on /var/log and also the whole file system. It didn't find any strings matching the USB drive's barnd name.  I also ran the string "USB". There were matches referencing "connection" of a USB device, but no identifying information on the device. 

I wonder if this is a definitive answer there's no identifying info on connected devices? As mentioned, Windows is quite different- the brand names for connected USBs and other devices are recorded all over the registry and elsewhere.

---

### Post by buzzingrobot on 2015-12-05
I just plugged a USB stick into this machine and dmesg instantly displayed:
> 
[105844.874256] usb 1-8: new high-speed USB device number 14 using xhci_hcd
[105845.039207] usb 1-8: New USB device found, idVendor=0781, idProduct=5530
[105845.039217] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[105845.039221] usb 1-8: Product: Cruzer
[105845.039224] usb 1-8: Manufacturer: SanDisk
[105845.039227] usb 1-8: SerialNumber: 200435129218D4F22EBB
[105845.040609] usb-storage 1-8:1.0: USB Mass Storage device detected
[105845.040792] scsi host6: usb-storage 1-8:1.0
[105846.042718] scsi 6:0:0:0: Direct-Access     SanDisk  Cruzer           1.20 PQ: 0 ANSI: 5
[105846.043180] sd 6:0:0:0: Attached scsi generic sg5 type 0
[105846.044026] sd 6:0:0:0: [sdd] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
[105846.044761] sd 6:0:0:0: [sdd] Write Protect is off
[105846.044768] sd 6:0:0:0: [sdd] Mode Sense: 43 00 00 00
[105846.045123] sd 6:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[105846.052866]  sdd: sdd1 sdd2 sdd3
[105846.055032] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[105846.456173] ISO 9660 Extensions: Microsoft Joliet Level 3
[105846.466693] ISO 9660 Extensions: RRIP_1991A




Being able to learn when someone has been plugging drives, USB or otherwise, into their networks is exactly the kind of thing a system administrator expects from an OS.

---

