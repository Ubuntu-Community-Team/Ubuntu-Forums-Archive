---
title: "Vivitar 3105s vai USB"
date: 2013-09-02
forum: New to Ubuntu
---

### Post by simon2 on 2013-09-02
Hi, up until 2 weeks ago, I could plug my Vivitar digital camera (model 3105s), into my laptop which would recognise the camera's disc and allow me to manipulate it. Now however, I cannot see the camera except via '*dmesg'*.  I cannot see it in either  File Manager or Disks.

Please find specifications and messages below:

```
$ uname --all
Linux simon-Aspire-5315 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 19:40:39 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

$ lsb_release --all
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring

$ lsusb
Bus 006 Device 002: ID 0784:1693 Vivitar, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ dmesg
[ 3443.752049] usb 5-1: new full-speed USB device number 2 using uhci_hcd
[ 3443.952083] usb 5-1: New USB device found, idVendor=0784, idProduct=1693
[ 3443.952089] usb 5-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 3443.952093] usb 5-1: Product: ViviCam 3105s           
[ 3443.952095] usb 5-1: Manufacturer: Vivitar          
[ 3443.955277] scsi5 : usb-storage 5-1:1.0
[ 3444.966106] scsi 5:0:0:0: Direct-Access     Vivitar  ViviCam 3105s    0001 PQ: 0 ANSI: 0
[ 3444.966625] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 3444.987089] sd 5:0:0:0: [sdb] 4000 512-byte logical blocks: (2.04 MB/1.95 MiB)
[ 3444.993081] sd 5:0:0:0: [sdb] Write Protect is off
[ 3444.993086] sd 5:0:0:0: [sdb] Mode Sense: 07 00 00 00
[ 3444.998080] sd 5:0:0:0: [sdb] No Caching mode page present
[ 3444.998084] sd 5:0:0:0: [sdb] Assuming drive cache: write through
```

Does anyone have any ideas as to how I can access the camera's SSD again?

Thanks, Simon.

---

### Post by GwL3eNC on 2013-09-02
Hi Simon2,

i can't tell you why your system stopped auto mount you camera. Have you tried to mount
the SSD manualy. If i understand the dmesg your SSD card is known as sdb. Now you
can try it like that. Fist you need to know the file system type of the SSD card

sudo blkid -o list -w /dev/null 

shows it. I assume it's vfat.
Then make a new folder camera as mount point to use

mkdir camera

Then mount the SSD 

sudo mount -t vfat /dev/sdb1 camera

If it works you can see all stuff from SSD in the camera folder. If you are ready unmount the device

sudo umount /dev/sdb1

or sudo umount camera (not shure, one of them)

Dont unplug the device without umount!

---

