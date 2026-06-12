---
title: "How do you ask Ubunut to scan hard drive for errors?"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by etrexuser on 2012-05-05
How do you ask Ubuntu to scan Hard Drive for errors without an Ubuntu CD?

---

### Post by datenhalde on 2012-05-05
The tool you need would be fsck.ext4 (assuming you use ext4 as your file system). See man fsck for options. But afaik there's no way to do it on a mounted disk. You can either, if that's possible with the partition in question, umount it and use fsck on the device (say /dev/sdaN), or if that'd mean umounting a system disk in use, reboot into single user or recovery mode and then start fscking. If you have only one partition, better use a live CD.

---

### Post by CharlesA on 2012-05-05
> **etrexuser said:**
> How do you ask Ubuntu to scan Hard Drive for errors without an Ubuntu CD?
```
sudo touch /forcefsck
```

Reboot and let it do its thing.

---

### Post by etrexuser on 2012-05-05
sorry, that does not seem to do anything

---

### Post by etrexuser on 2012-05-05
> **datenhalde said:**
> The tool you need would be fsck.ext4 (assuming you use ext4 as your file system). See man fsck for options. But afaik there's no way to do it on a mounted disk. You can either, if that's possible with the partition in question, umount it and use fsck on the device (say /dev/sdaN), or if that'd mean umounting a system disk in use, reboot into single user or recovery mode and then start fscking. If you have only one partition, better use a live CD.

I just ordered version 12.x lts from Canocial disks to be shipped to me in the U.S.  I think my HD is on the blink or something.  See my thread in the hardware section as something is unstable about my system.

[http://ubuntuforums.org/showthread.php?t=1973994](http://ubuntuforums.org/showthread.php?t=1973994)

---

### Post by Hadaka on 2012-05-05
You can also select the dash button,then more aps,then disk utility.
there you can mount..format..test.partition  ,scan for erroros whatever.

hope this helps

---

### Post by jerome1232 on 2012-05-05
> **etrexuser said:**
> sorry, that does not seem to do anything

The touch command creates a file called forecefsck on the root of your drive, the next time your computer is booted, that file will be detected and a fsck will be run during the boot process.

---

### Post by duncan12 on 2012-05-05
Is it the "Check Filesystem" option here?

Dash -> Disk Utility

---

### Post by jerome1232 on 2012-05-05
> **duncan12 said:**
> Is it the "Check Filesystem" option here?

Dash -> Disk Utility

You can't check it while the system is running, do the touch command, and reboot, it will check the file system during the boot process.

---

### Post by etrexuser on 2012-05-05
> **jerome1232 said:**
> You can't check it while the system is running, do the touch command, and reboot, it will check the file system during the boot process.


ok, it checked upon boot and didn't report anything wrong.  So I wonder why my operating system is having such problems with adobe flash and reporting such problems

---

### Post by etrexuser on 2012-05-05
> **duncan12 said:**
> Is it the "Check Filesystem" option here?

Dash -> Disk Utility


I will have to wait for my Ubuntu disks to come in, trying that gives
"Device is mounted and no online capability in fsck tool for file system"

---

### Post by Hadaka on 2012-05-05
from dash-more apps-disk utility- then click on hard drive- on the right is
smart data..thats where you can run tests and you can also run check file
system to look for bad sectors and hopefully repair if any errors are found.
you mentioned something about "flashplayer" what errors or outmessage
are you getting that makes you suspect hard drive problems??

---

### Post by Hadaka on 2012-05-05
ok..so i bounced over to your other post..which is basically the same problem
so it makes it confusing to post twice for the same related issue. try the software
center for adobe flash..paying close attention to your ubuntu version. 
good luck

---

