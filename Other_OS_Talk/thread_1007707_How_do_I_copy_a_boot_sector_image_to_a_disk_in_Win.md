---
title: "How do I copy a boot sector image to a disk in Windows?"
date: 2008-12-10
forum: Other OS Talk
---

### Post by init1 on 2008-12-10
This is very easily done in in Linux (dd if=file.img of=/dev/disk) and DOS (there's an app called BOOTMGR which does this) but I can't figure out how in Windows. I tried a Windows dd port, but it didn't work (the file was most likely copied to the start of the partition, rather than the start of the disk). Anyone know how?

---

### Post by caljohnsmith on 2008-12-10
Maybe this program would help:

[http://www.nu2.nu/mkbt/](http://www.nu2.nu/mkbt/)

But why not just copy the boot sector from a Live CD with dd? What is your ultimate goal?

---

