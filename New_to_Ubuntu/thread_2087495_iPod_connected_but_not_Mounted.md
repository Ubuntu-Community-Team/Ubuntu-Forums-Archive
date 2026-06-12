---
title: "iPod connected but not Mounted"
date: 2012-11-23
forum: New to Ubuntu
---

### Post by MathiasR on 2012-11-23
Preface: I'm using Xubuntu 11.10 and the iPod in question is an iPod Classic 160gb. 

Hi, I've come across this problem rather recently and despite my best efforts, haven't been able to come up with a solution.

When I plug my iPod into my computer's usb drive, the screen of the iPod reads "Connected", and shows a frozen clock. However, the device is recognized by Xubuntu,  and appears in lsusb and blkid. The problem is that I'm not getting the typical "iPod was mounted automatically" popup I usually get, and am unable to get the device to mount. I've tried a few things I've read elsewhere on these forums, but to no avail. 

For reference, here is the iPod's blkid entry:
/dev/sdn1: LABEL="MATHIAS' IP" UUID="3141-5926" TYPE="vfat" 

Exactly what am I doing wrong, and how might I fix it?

---

### Post by windscape on 2012-11-23
Hi,

I had a similar issue with DVDs and Blu-Ray discs in Xubuntu 12.10. I resolved it by using the udevil package and the devmon automounting daemon included with it. I also had to add an entry to /etc/fstab so the mountpoint was consistent. You can get udevil from here: [http://ignorantguru.github.com/udevil/](http://ignorantguru.github.com/udevil/)

---

