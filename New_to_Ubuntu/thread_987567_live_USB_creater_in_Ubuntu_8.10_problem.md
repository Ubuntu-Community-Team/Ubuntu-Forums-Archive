---
title: "live USB creater in Ubuntu 8.10 problem"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by cheeseman52 on 2008-11-19
ok so I downloaded an ubuntu 8.10 ISO, burned the image to a disk, booted off the disk, plugged in my 2gb flash drive, and used the live usb creator without any problems.  However, when I try to boot off of the flash drive I always get the same error which reads

[    0.262286] ACPI: Aborted because junk is in compressed archive.
[    1.869634] crc error
[    1.909618] Kernel Panic - not syncing: VFS: Unabe to mount root fs on unknown-block(8,1)

please help me get this up and running

---

### Post by Shwefty on 2008-11-19
Same .iso image?  Did you make sure and check the md5sum?

---

### Post by cheeseman52 on 2008-11-19
yes I am sure that I used the correct iso.  I'm pretty new to this so you will have to explain what md5sum is.

---

### Post by C.S.Cameron on 2008-11-19
usb-creator seems to get fussy with the formatting on some flash drives.
Try UNetbootin, It seems to have a way with formatting flash drives.
If it works and you still want a usb-creator persistence install, erase the UNetbootin files and try U-C again. It likes flash drives that have been previously set up with UNebootin.

---

### Post by cheeseman52 on 2008-11-21
Ok I reformatted the flash drive and used UNetbootin to make a boot able ubuntu.  That didn't work so i erased all the files off the drive and used the live usb creator in ubuntu 8.10.  Now when i try to boot i get...

system halted crc error


any ideas?

---

### Post by Jakey_TheSnake on 2009-03-11
I get the same error, bump. 

I've done a LOT to get even this far, there seems to be some annoying bugs with the LiveUSB Creator.

---

### Post by sbarrow on 2009-09-19
I had this same issue on an HP dx5150 SFF. I had two identical 5150's, one booted fine, the other, not so fine. turns out it was either some bad RAM or a memory resident virus. Once I removed two of the four RAM modules it worked fine. If anyone can point me to a way to 'clear' any memory resident viruses on RAM that would be great.

---

