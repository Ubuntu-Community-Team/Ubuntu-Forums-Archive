---
title: "usb Flash Drive is Read Only"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by 4835jack on 2012-10-06
This is a fairly new 64GB  flash drive that worked fine until today. Now it is read only. I tried  to format but it won't let me. I have been reading related problems for  hours and have tried many things but nothing works. Can someone please  help? I ran  dmseg in the terminal and got this. The drive is formated  as FAT32


  4869.435205] wlan0: authenticated [ 4869.444382] wlan0: associate with 00:02:6f:57:50:fe (try 1) [ 4869.447207] wlan0: RX ReassocResp from 00:02:6f:57:50:fe (capab=0x421 status=0 aid=2) [ 4869.447216] wlan0: associated [ 5296.184306] usb 1-2: USB disconnect, device number 4 [ 7678.712155] usb 1-3: new high-speed USB device number 5 using ehci_hcd [ 7678.847220] scsi8 : usb-storage 1-3:1.0 [ 7680.313009] scsi 8:0:0:0: Direct-Access     PNY      USB 2.0 FD       1100 PQ: 0 ANSI: 4 [ 7680.313921] sd 8:0:0:0: Attached scsi generic sg2 type 0 [ 7680.319848] sd 8:0:0:0: [sdb] 127835904 512-byte logical blocks: (65.4 GB/60.9 GiB) [ 7680.320498] sd 8:0:0:0: [sdb] Write Protect is on [ 7680.320504] sd 8:0:0:0: [sdb] Mode Sense: 43 00 80 00 [ 7680.321090] sd 8:0:0:0: [sdb] No Caching mode page present [ 7680.321095] sd 8:0:0:0: [sdb] Assuming drive cache: write through [ 7680.321100] sd 8:0:0:0: [sdb] Attached SCSI removable disk [ 7680.334384] sd 8:0:0:0: [sdb] No Caching mode page present [ 7680.334395] sd 8:0:0:0: [sdb] Assuming drive cache: write through [ 7680.337135] sd 8:0:0:0: [sdb] No Caching mode page present [ 7680.337143] sd 8:0:0:0: [sdb] Assuming drive cache: write through [ 7680.338187]  sdb: sdb1

---

### Post by dniMretsaM on 2012-10-06
Unmount the device ([FONT=Courier New]sudo umount /dev/xxxy[/FONT]) and run this:
```
sudo dosfsck -a /dev/xxxy
```

Replace "xxxy" with the name of the USB device and the partition number. (i.e. "sdb1").

That will check the integrity of the drive and fix any issues it finds. Then you might be able to mount it as read/write.

---

### Post by 4835jack on 2012-10-06
So I ran the command and this is what I got.

jack@jackslife:~$ sudo dosfsck -a /media/JacksLife sdb1
usage: dosfsck [-aAflrtvVwy] [-d path -d ...] [-u path -u ...]
               device
  -a       automatically repair the file system
  -A       toggle Atari file system format
  -d path  drop that file
  -f       salvage unused chains to files
  -l       list path names
  -n       no-op, check non-interactively without changing
  -p       same as -a, for compat with other *fsck
  -r       interactively repair the file system
  -t       test for bad clusters
  -u path  try to undelete that (non-directory) file
  -v       verbose mode
  -V       perform a verification pass
  -w       write changes to disk immediately
  -y       same as -a, for compat with other *fsck
jack@jackslife:~$ 

What am I doing wrong?

---

### Post by ajgreeny on 2012-10-06
Do not use the mountpoint path for the device as you did with```
sudo dosfsck -a /media/JacksLife sdb1
``` just use the device's name, sdb1```
sudo dosfsck -a /dev/sdb1
```

Finally, do you have the **usbmount** package installed?  If so remove it as it is not needed and can cause this problem.

---

### Post by 4835jack on 2012-10-06
OK did this.

jack@jackslife:~$ sudo dosfsck -a /dev/sdb1
[sudo] password for jack: 
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
open: Read-only file system
jack@jackslife:

How do I find out if I have the **usbmount** package installed? and how do I delete it if I do?

---

### Post by ajgreeny on 2012-10-06
Use command ```
whereis usbmount
``` in terminal. If installed you will get output like ```
usbmount: followed by a list of pathways
```if not installed just ```
usbmount:
```
You could also run ```
sudo apt-get remove usbmount
```

---

### Post by 4835jack on 2012-10-06
OK usbmount is not installed. Did I say that this is 12.04

---

