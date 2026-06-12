---
title: "USB Flash speed"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by temida on 2012-11-15
hi! How can i test usb flash speed (write/read) :cry:in linux ?

---

### Post by newb85 on 2012-11-15
Don't know about write speed, but you can test read speed like this:

Use this command to determine the device address of your drive:
```
sudo fdisk -l
```

Then issue:
```
sudo hdparm -t /dev/sda1
```
replacing /dev/sda1 with the address of the flash drive.

Edit:  If the drive is empty, you can use Disk Utility (installed by default) to Benchmark the drive.

Edit 2: "Empty" as in absolutely nothing on the drive, including partition table.  This can be achieved with Disk Utility, as well.

---

### Post by temida on 2012-11-15
thank you :) i will try

---

### Post by temida on 2012-11-17
it doesn`t work  or maybe i can`t do it ...   first i open console with ctrl +alt +f1 than i write 
```
sudo fdisk -l
sudo hdparm -t /dev/media/traxdata 
``` ( /media/traxdata -adress of the flash drive)...
i found code for write test but i dont know how to work with this code ...
Create a file system, if necessary:
```
$ sudo mkfs.vfat /dev/sdb1
```
Test:
```
$ sudo mount /dev/sdb1 /media/misc
$ sudo dd count=100 bs=1M if=/dev/zero of=/media/misc/testfile.raw oflag=sync
```

---

### Post by newb85 on 2012-11-17
Instead of 
```
sudo hdparm -t /dev/media/traxdata
```
you should have used 
```
sudo hdparm -t /media/traxdata
```

As a side note, when you are posting terminal commands or output, you should highlight it in the post composition frame and click the "#" button above the frame to wrap it in [CODE] tags.  It makes posts more readable.

---

### Post by C.S.Cameron on 2012-11-17
Copy a one gig file to the flash drive, how long did that take?
Copy a one gig file from the flash drive, how long did that take?
Divide one thousand by your answers and that will give the write and read speeds in MB/s .

---

### Post by valentt on 2013-09-22
I made a detailed blog post regarding this topic:
[http://kernelreloaded.blog385.com/index.php/archives/benchmark-flash-memory-on-linux/](http://kernelreloaded.blog385.com/index.php/archives/benchmark-flash-memory-on-linux/)

---

