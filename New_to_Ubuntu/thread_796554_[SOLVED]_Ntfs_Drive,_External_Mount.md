---
title: "[SOLVED] Ntfs Drive, External Mount"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by k33bz on 2008-05-16
Anyone know how to mount a harddrive that is ntfs format. its usually a internal harddrive, but i am using this device to make it an exteranl drive. Works wonderful for my drive that has Ubuntu on it, but kant see my windoze hdd.[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2329300&Sku=M501-1220]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2329300&Sku=M501-1220")

---

### Post by az on 2008-05-16
I have a few of those.  I use them for data recovery.  Your NTFS filesystem should be mounted automatically in Ubuntu just like any other filesystem.

Open the log tool and loog at the messages log.  Plug in the device.  What does the log say then?

---

### Post by k33bz on 2008-05-16
where is the log tool at?

and my ntfs is set to automatic detection. but it wont pop up, an dlooked for it manually

---

### Post by k33bz on 2008-05-16
Bump

---

### Post by steve-shinn on 2008-05-16
System>Administration>System Log

---

### Post by k33bz on 2008-05-16
ok, here is what i get with it plugged-in and on

```
messages
May 16 15:07:05 K33bz-mobile kernel: [  465.452000] usb 5-2: new high speed USB device using ehci_hcd and address 6
May 16 15:07:06 K33bz-mobile kernel: [  465.584000] usb 5-2: configuration #1 chosen from 1 choice
May 16 15:07:06 K33bz-mobile kernel: [  466.048000] scsi3 : SCSI emulation for USB Mass Storage devices
May 16 15:07:11 K33bz-mobile kernel: [  471.048000] scsi 3:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
May 16 15:07:11 K33bz-mobile kernel: [  471.048000] sd 3:0:0:0: Attached scsi disk sdb
May 16 15:07:11 K33bz-mobile kernel: [  471.048000] sd 3:0:0:0: Attached scsi generic sg2 type 0

syslog
May 16 15:07:05 K33bz-mobile kernel: [  465.452000] usb 5-2: new high speed USB device using ehci_hcd and address 6
May 16 15:07:06 K33bz-mobile kernel: [  465.584000] usb 5-2: configuration #1 chosen from 1 choice
May 16 15:07:06 K33bz-mobile kernel: [  466.048000] scsi3 : SCSI emulation for USB Mass Storage devices
May 16 15:07:06 K33bz-mobile kernel: [  466.048000] usb-storage: device found at 6
May 16 15:07:06 K33bz-mobile kernel: [  466.048000] usb-storage: waiting for device to settle before scanning
May 16 15:07:11 K33bz-mobile kernel: [  471.048000] usb-storage: device scan complete
May 16 15:07:11 K33bz-mobile kernel: [  471.048000] scsi 3:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
May 16 15:07:11 K33bz-mobile kernel: [  471.048000] sd 3:0:0:0: Attached scsi disk sdb
May 16 15:07:11 K33bz-mobile kernel: [  471.048000] sd 3:0:0:0: Attached scsi generic sg2 type 0
```

---

### Post by k33bz on 2008-05-16
when i type lsusb i get this, please not the firs one listed s the hdd in question.

```
keebler@K33bz-mobile:~$ lsusb
Bus 005 Device 007: ID 152d:2338  
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 002 Device 003: ID 06a3:8020 Saitek PLC 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

---

### Post by k33bz on 2008-05-16
bump

---

### Post by das letzte einhorn on 2008-05-16
I also do have an issue related to an external drive which is NTFS. It contains my document backup from Windows which I want to merge in Ubuntu and then format to ext3. I have posted a screenshot of the message which pops up.

---

### Post by k33bz on 2008-05-16
ok, for the most part i got mine working. tested on several of the hdd i have here. Didnt work with one however. my personal hdd from my desktop. it is running windoze, and i cant boot into it from my desktop at the moment. (it is being fixed). It pretty much says that i cant mount it because it was shut down improperly. does anybody know how i can work around this?

---

