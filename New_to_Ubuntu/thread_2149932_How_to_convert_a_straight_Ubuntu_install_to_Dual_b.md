---
title: "How to convert a straight Ubuntu install to Dual boot?"
date: 2013-05-30
forum: New to Ubuntu
---

### Post by bayouborne on 2013-05-30
Is there any way to convert what is currently a straight Ubuntu install to Dual boot? In a perfect world I wouldn't have to destroy the current Ubuntu load on this server, since I have a big application already loaded on it (Instructure/Canvas).

When I installed Ubuntu I believe I told it to take the whole disk when it asked its partitioning question.

Thanks!

Tom

---

### Post by ShadowVegan on 2013-05-30
From what I have heard, Windows is pretty uncooperative with this and wants to take up the whole HDD. If you try to install Windows second you will likely mess things up. However, it is possible. Make sure you back up your home folder if you have any files you want to save. For information on installing Windows second, see [here](https://help.ubuntu.com/community/WindowsDualBoot#Installing_Windows_After_Ubuntu).

---

### Post by Mark Phelps on 2013-05-30
You will have to boot from an Ubuntu LiveCD or LiveUSB and use GParted to shrink the partitions down to make some room.  You might have to select the Swap partition and choose SwapOFF to unmount it.  Do NOT use GParted to create a new partition in the empty space. Windows versions newer than Vista work best when their partitions are formatted using MS Windows.

Then, when you boot from the Windows install DVD, select the empty space -- and Windows will do its own partitioning.  Unlike rumours you may have heard, it will NOT wipe out the remainder of the drive.

When you reboot, since Windows overwrote the GRUB entry in the MBR, you will boot directly into Windows. Follow instructions in the link to get access to Ubuntu back:  [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by bayouborne on 2013-05-30
[HR][/HR]Excellent, excellent - thank you both!!

Tom

---

