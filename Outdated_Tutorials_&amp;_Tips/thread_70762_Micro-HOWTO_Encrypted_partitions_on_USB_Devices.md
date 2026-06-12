---
title: "Micro-HOWTO: Encrypted partitions on USB Devices"
date: 2005-10-01
forum: Outdated Tutorials &amp; Tips
---

### Post by mercurus on 2005-10-01
Greetings
This has only been tested on Breezy Preview, but I didn't think it deserved posting in the Breezy Devel Forum.
This is largely a re-hash of a post to the Ubuntu-Developers mailing list from Martin Pitt ( [http://www.ubuntuforums.org/showthread.php?t=49474](http://www.ubuntuforums.org/showthread.php?t=49474) ) with some additional information about partitioning USB devices.
THIS IS NOT FOR THE NOVICE, READ ON ONLY IF YOU'RE HAPPY BREAKING THINGS AND KEEPING BOTH PIECES. Please be aware that you could easily lose data, or murder USB thumbdrives with these instructions. Unless you are prepared to take the risk, DON'T!
I bought a 256 MB Thumbdrive and plugged it into my machine, receiving the following output in dmesg:
```
[4294935.528000] usb 1-1: new full speed USB device using uhci_hcd and address 2
[4294936.147000] SCSI subsystem initialized
[4294936.181000] Initializing USB Mass Storage driver...
[4294936.195000] scsi0 : SCSI emulation for USB Mass Storage devices
[4294936.199000] usb-storage: device found at 2
[4294936.199000] usb-storage: waiting for device to settle before scanning
[4294936.200000] usbcore: registered new driver usb-storage
[4294936.200000] USB Mass Storage support registered.
[4294941.203000]   Vendor:           Model: USB DISK Pro      Rev: PMAP
[4294941.203000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294941.224000]   Vendor:           Model: USB DISK Pro      Rev: PMAP
[4294941.224000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4294941.241000] usb-storage: device scan complete
[4294941.833000] SCSI device sda: 489472 512-byte hdwr sectors (251 MB)
[4294941.836000] sda: Write Protect is off
[4294941.837000] sda: Mode Sense: 23 00 00 00
[4294941.837000] sda: assuming drive cache: write through
[4294941.853000] SCSI device sda: 489472 512-byte hdwr sectors (251 MB)
[4294941.856000] sda: Write Protect is off
[4294941.856000] sda: Mode Sense: 23 00 00 00
[4294941.856000] sda: assuming drive cache: write through
[4294941.857000]  /dev/scsi/host0/bus0/target0/lun0: p1 p2
[4294941.872000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4294941.882000] SCSI device sdb: 2880 512-byte hdwr sectors (1 MB)
[4294941.885000] sdb: Write Protect is off
[4294941.885000] sdb: Mode Sense: 23 94 00 00
[4294941.885000] sdb: assuming drive cache: write through
[4294941.903000] SCSI device sdb: 2880 512-byte hdwr sectors (1 MB)
[4294941.905000] sdb: Write Protect is off
[4294941.905000] sdb: Mode Sense: 23 94 00 00
[4294941.905000] sdb: assuming drive cache: write through
[4294941.906000]  /dev/scsi/host0/bus0/target0/lun1:
[4294941.919000] Attached scsi removable disk sdb at scsi0, channel 0, id 0, lun 1

```
I knew that the usb key I bought had some "locking" software included, so that you could lock the key in Windows. I've got my doubts about the utility of this software. Either way, there are two devices in the one physical device:
```
/dev/sda1
/dev/sdb

```
Both of these appeared on my desktop when I inserted the device. sda1 was 251MB and sdb was 1MB and contained a Win32 .exe binary, and a pdf instruction book on using the locking software.
(I didn't test it, but surely the lock is software only - and you could simply reboot to another operating system and manually mount the usbdisk, and access the data ..?)
Having worked out what was on the usb drive, and knowing what I wanted to have on there, I used gparted to repartition the usb drive as follows:
```
/dev/sda1 - 5 MB (ext2)
/dev/sda2 - 50 MB (ext2)
/dev/sda3 - remainder (vfat)
```
I wanted to use the first 5 MB of the drive as a secure storage space for my SSH and GPG keys, the next 50 MB of the drive as a secure data backup space for some sensitive documents and the remainder of the drive for everyday use.
I now began following Martin's instructions and installed the cryptsetup package. Then I ran: sudo luksformat -t ext2 /dev/sda1 && sudo luksformat -t ext2 /dev/sda2 . I chose different passphrases for each section of the usb drive. 
Now I edited my /etc/fstab file and commented out all existing sda-related entries. (If you leave them in, even with the "auto" fs type, the gnome-volume-manager dialog that requests your passphrase to access the device will crash - I should submit a bug about this)
With this done, unmount the device (if necessary), then remove and re-insert the device. You should have two partitions mount (sda3 and sdb) and two dialog boxes asking for passphrases. How you tell which is which, is beyond me ... good luck ;)
I'm going to look at expanding this documentation to include some of the information provided about using SSH and GPG keys for authentication, some of the usbpam information, and this information about changing Volume IDs: [http://www.ubuntuforums.org/showthread.php?t=70741](http://www.ubuntuforums.org/showthread.php?t=70741)
Hope this helps someone, but PLEASE, PLEASE, PLEASE remember that you could very easily lose data, kill your usb device, or lock yourself out of your data. BE CAREFUL !
Cheers
mercurus

---

### Post by mercurus on 2005-10-01
I've just finished combining the above Micro-HOWTO with the Mini-HOWTO on using pam_usb - works very nicely. Will post soon !

Cheers
mercurus

---

