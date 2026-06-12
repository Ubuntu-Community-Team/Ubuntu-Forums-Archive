---
title: "iPod not working with Ubuntu"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Christian91 on 2008-05-19
Hey guys, have a slight problem here with my ipod. When i plug in to my computer it can't find it. There is not the icon on the desktop and i can't find it any where in the file system so i can't sync songs to it ? Any one got an idea on how to solve this ?

---

### Post by chamberlain2006 on 2008-05-19
Is this a new iPod? (ie, iPod classic, the new iPod nano, or the iPod touch)  Apple changed how the iPods connect to computers when they made these new iPods, and they currently don't work on Linux.

---

### Post by tamoneya on 2008-05-19
what are you using for organizing your music in linux.  Also post the result of```
sudo fdisk -l
```
It is probably easier to use gtkpod instead of itunes+wine

---

### Post by Christian91 on 2008-05-19
Yes , it's an iPod Touch. So this means that i just can't use it at all ?

---

### Post by mmb1 on 2008-05-19
No, I'm sure there's a workaround , try downloading "gtkpod", from synaptic, and using it.  Also, I reccomend searching the forums, there's a wealth of info out there.

---

### Post by Christian91 on 2008-05-19
I use rythmbox

This is the reply i get:

christian@christian-laptop:~$ sudo fdisk -l
[sudo] password for christian: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x69c369c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

---

### Post by chamberlain2006 on 2008-05-19
The iPod touch won't work with Ubuntu.  It's known to be fact, plus I own one and can attest to that fact.  It is possible to do it wirelessly, but it is not officially supported, and requires a jailbroken iPod.

---

### Post by xeth_delta on 2008-05-19
> **chamberlain2006 said:**
> Is this a new iPod? (ie, iPod classic, the new iPod nano, or the iPod touch)  Apple changed how the iPods connect to computers when they made these new iPods, and they currently don't work on Linux.

That was indeed the case. I believe it was already solved for the classic and nano versions. I have a new nano, it works.
That said, I use Amarok to transfer music to it.

---

### Post by Christian91 on 2008-05-19
My Touch is jailbroken, is it easy to do it wirelessly ?

---

### Post by Tom--d on 2008-05-19
The iPod Touch and the iPhone have new firmware and Linux cannot dectect the device. 

I heard people have corrected this. Search around.

Also, you can go on the safe side:

Use Windows in VirtualBox (run a os in a os) and you can get usb support and.. iTunes :P
Then it will work :D

---

### Post by chamberlain2006 on 2008-05-19
I wouldn't say easy, but possible.  Instructions are here: [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone).

---

