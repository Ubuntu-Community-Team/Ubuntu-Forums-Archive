---
title: "Grub Rescue Problem"
date: 2016-05-01
forum: New to Ubuntu
---

### Post by owen.m16outlook.c on 2016-05-01
So, I recently changed my partition to try to boot to Windows 8, which didn't work (I don't think I have Windows 8 anymore...), and now I just get the message:
"error: no such partition
grub rescue>"

I've tried the 'ls' command and come up with 3 drives, all come back with 'no filesystem'. I don't know what to do anymore. Also, when I try to change from Legacy Bios to UEFI, it won't let me, and I cannot change any other settings. A solution to this problem would also be helpful.

---

### Post by oldrocker99 on 2016-05-01
If you want to dual-boot, install Windows **first**. Then Grub will properly work, allowing you to select Windows or Linux. Installing Windows to dual-boot with an existing Linux installation frequently results in the kind of errors you're getting.

Hopefully, your data is backed up.

---

### Post by yancek on 2016-05-01
What exactly does 'changed my partition' mean and how did you do this?  You can boot the Ubuntu Live DVD and run the command:  sudo fdisk -l(Lower Case Letter L in the command) and post that here which will show drive/partition info.

---

