---
title: "Error mounting /dev/sda2 at/media/zuber/Data:wrong fs type"
date: 2023-07-24
forum: New to Ubuntu
---

### Post by nope777 on 2023-07-24
Error mounting /dev/sda2/ at media/user/Data :wrong fs type ,bad option ,bad superblock on /dev/sda2/,missing codepage or helper program or other error 

this is the error i am getting while accessing my hard drive

---

### Post by TheFu on 2023-07-24
Use the correct file system type.
Check for file system corruption.
Check for a failing storage device.

Hopefully, you have excellent backups.

---

### Post by yancek on 2023-07-24
What exactly are you doing to access the partition?  Using a file manager or terminal?  What filesystem type is it?  You can find that by using:  sudo parted -l which will list partitions and filesystem types.  If it is Linux, use fsck.  If it is windows use chkdsk.

---

