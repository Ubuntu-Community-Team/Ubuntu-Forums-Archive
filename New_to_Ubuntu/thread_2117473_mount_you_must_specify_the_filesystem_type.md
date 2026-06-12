---
title: "mount: you must specify the filesystem type"
date: 2013-02-18
forum: New to Ubuntu
---

### Post by mcflied on 2013-02-18
I get this error message when trying to mount second hard drive.

# sudo mount /dev/xvdc1 /media/30GBHD

mount: you must specify the filesystem type

# sudo mount /dev/xvdc1 -t ext4 /media/30GBHD

mount: wrong fs type, bad option, bad superblock on /dev/xvdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Any ideas?  Thank you in advance.

---

### Post by Mark Phelps on 2013-02-18
I believe the format is:

> # sudo mount /dev/xvdc1 /media/30GBHD -t ext4

---

### Post by vanadium on 2013-02-18
Probably indeed the format of the command: the option must come before or after the device and mount point, not inbetween.

If this message is thrown using a valid command, then that indicates that something is wrong with the file system. With the command
```

dmesg | tail -n 30

```
you can see kernel messages, which may give a hint of what is wrong.

---

### Post by SeijiSensei on 2013-02-18
The OS really does not see an ext4 filesystem on /dev/xvdc1. I'm usually brought up short by this message, but Linux doesn't lie about things like this.  On good days it means I'm not addressing the right device.  On bad days, well, we'll leave that aside for the moment.  What does "sudo fdisk -l" show?

---

