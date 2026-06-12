---
title: "Mount point 0 does not exist."
date: 2018-09-16
forum: New to Ubuntu
---

### Post by itechstr on 2018-09-16
I have been trying to mount an usb drive to my raspberry, but suddenly i started getting the same error over and over and I couldn't find a single way to fix this.


> mount: /etc/fstab: parse error at line 3 -- ignored
mount: mount point 0 does not exist


And this is the fstab file:


 - proc /proc proc defaults 0 0
 - /dev/mmcblk0p6 /boot vfat defaults
 - 0 2 /dev/mmcblk0p7 / ext4
 - defaults,noatime 0 1
 - #### a swapfile is not a swap partition, no line here
 - #### use  dphys-swapfile swap[on|off]  for that
 - UUID=E6A0-4042 /media/usb1 auto nofail,uid=1000,gid=1000,noatime 0 0


Thanks in advance.

---

### Post by The Cog on 2018-09-16
DON'T REBOOT!

Will post more in a moment.

---

### Post by The Cog on 2018-09-16
Your fstab file is mangled somehow. 
I really don't understand how you got the dashes at the start of each line. Are they really there?
Beyond the dashes, it looks as though a couple of new-lines have been moved.

Below is my guess at what the file should look like. However I am only guessing and could be wrong.
Unfortunately, getting the fstab file wrong will probably prevent the pi from booting.
My pi has a different looking fstab - it uses PARTUUID=... instead of /dev/... to identify the device partitions, but I don't think that's too important.
```
proc /proc proc defaults 0 0
/dev/mmcblk0p6 /boot vfat defaults 0 2 
/dev/mmcblk0p7 / ext4 defaults,noatime 0 1
#### a swapfile is not a swap partition, no line here
#### use dphys-swapfile swap[on|off] for that
UUID=E6A0-4042 /media/usb1 auto nofail,uid=1000,gid=1000,noatime 0 0
```

---

