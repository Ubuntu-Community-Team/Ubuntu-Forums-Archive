---
title: "external floppy disk drive problems"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by chris200x9 on 2008-06-28
Hi, I have an external floppy disk drive, it shows up on my desktop but when I double click it it says ```
 Given device "/org/freedesktop/Hal/devices/storage_serial_TEAC_TEAC_FD_05PUB" is not a volume or drive
``` 

I then put a disk in then when I double click it the same thing happens. I tried to manually mount but it said theres was no /dev/fd0. Any help?

---

### Post by Rocket2DMn on 2008-06-29
I've never tried mounting a floppy, but we'll give it a go.
With a disk in the drive, can you please post the output of
```
sudo fdisk -l
cat /etc/fstab
mount
sudo blkid
```

---

