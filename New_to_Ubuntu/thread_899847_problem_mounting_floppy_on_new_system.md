---
title: "problem mounting floppy on new system"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by jstateson on 2008-08-24
I built 8.0.4.1 x64 with no floppy thinking I did not need one. I picked up a usb floppy that I know works (windows) but cannot get it to mount on ubuntu.

lsusb shows the following

root@jyslinux3:/etc# lsusb
Bus 004 Device 005: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 057b:0000 Y-E Data, Inc. FlashBuster-U Floppy
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

poking around /dev I see the following:

/dev/usbdev1.1_ep00  /dev/usbdev3.1_ep81  /dev/usbdev4.1_ep00
/dev/usbdev1.1_ep81  /dev/usbdev3.3_ep00  /dev/usbdev4.1_ep81
/dev/usbdev2.1_ep00  /dev/usbdev3.3_ep02  /dev/usbdev4.5_ep00
/dev/usbdev2.1_ep81  /dev/usbdev3.3_ep81  /dev/usbdev4.5_ep01
/dev/usbdev3.1_ep00  /dev/usbdev3.3_ep83  /dev/usbdev4.5_ep82

I created /media/floppy0 using mkdir but I have no idea what to mount. I tried a bunch of the above 3_3 etc, and none worked.

I looked at /proc/bus/usb and did not see the expected 0 1 2 3 etc - nothing in that directory.

I added "floppy" to etc/modules and modprobe usb-storage does not return an error.

..thanks in advance..

---

### Post by DrPppr242 on 2008-08-24
haven't tried usb floppy drives before but floppies are usually under /dev/fd0, 'sudo ls /dev/fd*' will display detected floppy drives if none show up 'dmesg|grep fd' or if you use syslog 'sudo cat /var/log/messages.log|grep usb' might give you more info on what the problem is

---

