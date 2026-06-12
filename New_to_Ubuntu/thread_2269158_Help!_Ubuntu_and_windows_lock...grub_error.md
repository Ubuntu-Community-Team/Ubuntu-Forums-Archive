---
title: "Help! Ubuntu and windows lock...grub error"
date: 2015-03-13
forum: New to Ubuntu
---

### Post by jamesal777 on 2015-03-13
Hi, I'm new to Ubuntu and I have a problem that lock & unable my computer.
I´lI partitioned the disk for use by other windows and ubuntu without carefull.
Within windows delete the partition of ubuntu and when I restart the pc black screen appeared


error: no such partition
Entering rescue mode ...
grub rescue>


I have spent much time on this, I booted with ubuntu usb to reinstall and when I want to open "install ubuntu" I get the following: [http://i.4cdn.org/g/1426285668773.jpg](http://i.4cdn.org/g/1426285668773.jpg)


Can´t open ubuntu without installing. These lines after you remove are left without doing anything, apparently.


I tried installing windows 7 and windows 10 usb and dvd, but both stand still and I don't see the typical window where the keyboard language and system are chosen.


Then check on other sites and videos and noticed that they wrote in the grub rescue:


grub rescue> ls


and then I appear, I think, partitions:


(hd0) (hd0, msdos5), (hd0, msdos1)


I write each:


grub rescue> ls (hd0)
grub rescue> ls (hd0, msdos5)
grub rescue> ls (hd0, msdos1)


and I get something like file system unknown or something.


Don't know what else to do, I can not enter any operating system, I can not use the terminal ubuntu windows or by chance and much less. Do not know if this is correct to wait many hours to boot the setup both windows and ubuntu.


I don't mind erasing or formatting everything I had just to let me install any operating system. My laptop is Toshiba Satellite.


I count on another computer where I have pictures iso and burn to DVD or boot, it's the only thing or I can do write to the grub rescue. I have completely blocked the notebook, and any solution to this problem is the infinitely appreciate.


Thank you for read & answer my question.
Greetings!

---

### Post by yancek on 2015-03-13
If you were using the Ubuntu Grub bootloader to boot both windows and Ubuntu then deleting the partition with Ubuntu on it deleted necessary boot files.  The error no such partition is because it is looking for the partition which you deleted.  The unknown filesystem is probably because it is trying to mount to boot on a windows system rather than chainloading.  I don't know why you would not be able to reinstall windows and/or Ubuntu.

You could try downloading and running the boot repair script, select the option to Create Boot Info Summary then post the output here.  It's at the link below.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

