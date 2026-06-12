---
title: "usb flash drive not mounting"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by yard on 2008-07-09
I have a 1 gb flash drive that mounts fine on one machine and not on the other.  Both machines are running Hardy but the problem was the same when they ran Gutsy.  I can't mount manually because the drive does not show up in sudo fdisk -l. 

lsusb returns:

```
Bus 004 Device 006: ID 0781:5406 SanDisk Corp. Cruzer Micro 4GB Flash Drive
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 001: ID 0000:0000  

```

It shows up as a 4 gb but is really only 1.  The drive is Fat 32 and I have already tried reformatting, but to no avail.

Any suggestions?

---

### Post by ism. on 2008-07-09
i had a problem a little bit like that,  For a quick fix if your laptop/pc has more then one USB port try it in a different one because on one of my computers i could only plug it in twice per usb port.  Also you can check out this link
[http://ubuntuforums.org/archive/index.php/t-5184.html](http://ubuntuforums.org/archive/index.php/t-5184.html)
that might help your mount it.  Good luck and hope this helps (sorry if it doesn't)

-ism.

---

### Post by iaculallad on 2008-07-09
USB device filesystem might be in the error state so int can't be recognized by lsusb and can't be mounted.

Insert your USB flash drive on the Ubuntu machine that can properly recognize and mount it, then unmount it properly. Pull the USB flash drive and test in on the other system.

---

### Post by jgomo3 on 2008-07-09
on a terminal try

 $ tail -f /var/log/messages

before inserting the flash drive. Observe what happen when you plug it in. Look for "sdb:sdb1" or something like this.

It may help you if you read "sdb:sdb1" because you can mount it manually:

 $ sudo install -d /mount/flashdrive
 $ sudo mount /dev/sdb/sdb1 /mount/flashdrive

Or it may help to findout the root of the problem.

---

### Post by yard on 2008-07-09
Well, I've tried the drive in all ports, still the same.  Also the drive has been removed correctly from the other machine.

---

### Post by yard on 2008-07-09
jgomo3, tried what you suggested, when I inserted the drive I got:

```
Jul  9 22:54:58 shawn-desktop kernel: [ 9667.231945] usb 4-4: new high speed USB device using ehci_hcd and address 10
Jul  9 22:55:08 shawn-desktop kernel: [ 9677.367956] usb 4-4: configuration #1 chosen from 1 choice

```

---

### Post by kansasnoob on 2008-07-10
Not sure if this will help but it's easy and fully reversible. Try installing > usbmount from synaptic.

Either that or > pmount which, combined with hal, shows an icon on the desktop automatically anytime the drive's plugged in.

---

### Post by yard on 2008-07-10
tried both of those, still nothing.  I have a different flash drive which has always worked fine.  I don't know why this one is giving me problems.

---

### Post by yard on 2008-07-10
Problem solved! Finally found an old thread that addressed this issue: 

[http://ubuntuforums.org/showthread.php?t=207683&highlight=cruzer+micro+usb&page=2]("http://ubuntuforums.org/showthread.php?t=207683&highlight=cruzer+micro+usb&page=2")

After I did this:

```
sudo modprobe -r ehci_hcd
```

everything seems to work fine.  Thanks for the assistance!

:guitar:

---

