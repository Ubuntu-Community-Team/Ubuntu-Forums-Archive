---
title: "drive mounting permission"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by sammyray on 2008-11-10
I'm using Ubuntu 8.10 on a desktop. Computer says "unable to mount" when I select my USB connected floppy drive. In User Group permissions I have checked external devices but there is no specific selection for floppy. Any ideas?


Thanks,

SH:confused:

---

### Post by MasterSander on 2008-11-10
fire up a terminal and log in as root, create a dir where to mount the floppy drive, then search the device name in /dev, then type mount /dev/whatthenameofthedeviceis /path/to/dir/where/to/mount

---

