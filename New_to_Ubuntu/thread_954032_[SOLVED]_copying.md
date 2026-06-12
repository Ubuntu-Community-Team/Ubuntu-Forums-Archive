---
title: "[SOLVED] copying"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by johntravis on 2008-10-20
I am going to try to put a working ubuntu 8.04.1 on a usb stick using the command sudo dd if=/dev/sda of=dev/sdb. Is this the right command and how do you determine which is the hdd and which the usb (sda/sdb) Working means I am using the computer with ubuntu 8.04.1 installed.

---

### Post by johntravis on 2008-10-20
ok, I got the code from here and hoped the giver of this could explain how to define between usb/hdd

---

### Post by Pro-reason on 2008-10-20
Commands such as “sudo blkid -L” and “fdisk -l” can give you information about your drives, as can the GParted application.

---

