---
title: "[SOLVED] Help Please - Wireless on wife's computer - D-Link USB wireless"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by luckylucky on 2008-08-21
My wife has FINALLY taken the plunge into Ubuntu.  After years of hearing me hail how great it is she actually asked me to install it on her machine.  Bye bye Windows XP (and good riddance... it was annoyingly buggy, part of her reason for asking me to dump it).

Anyhow, I backed up all her files to external HD, and installed Ubuntu 8.04.1.  Hit first major road block...  I can't figure out how to connect her machine to the internet!

I have a wireless router to setup home networking for our computers, and for her machine I got (long time ago) a D-Link USB wireless adapter (model no.: WUA-2340).  Of course it had a disk to install the USB device in windows.  

The problem:

How do I get the USB wireless device working in Ubuntu so that this computer can have internet access?  It is the only way for it to get internet as it is not accessible by network cable.  

Please help, please please please

---

### Post by tuxulin on 2008-08-21
this looks pretty recent :)
[http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html](http://onlyubuntu.blogspot.com/2008/06/howto-setup-dlink-wua-2340-usb-wireless.html)

hope it helps

Tuxulin

---

### Post by luckylucky on 2008-08-21
This tutorial looks like the perfect solution. Thank you for directing me to this page.  I have another problem however...

How do I download the package files on a computer that doesn't have internet in the first place???  Hmmm... I've got a USB stick and another computer downstairs (the one I'm currently typing on, it has internet), so I will copy the files of the drivers to the USB stick to sneaker-net it onto the upstairs computer.

QUESTION:

The instructions say to apt-get the following:
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9

How can I download the files on another computer (this one is of course Ubuntu too) so that I can simply copy them to a USB stick?  Then, is there anything else I should know about how to install the packages onto the other computer from the USB location?  Can I just double click the files somehow, or do I install them by sudo ./whatever or some other method???

Thanks in advance for your reply!

---

### Post by forger on 2008-08-21
try on some computer with internet:

Download:
a) for **32-bit** Ubuntu:
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb)

or

b) for **64-bit** Ubuntu:
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.50-1ubuntu1_all.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.50-1ubuntu1_amd64.deb)

Download them to a usb stick, and double click on them to install them in the other computer

---

### Post by meindian523 on 2008-08-21
1]Copy the packages you download to your USB stick from /var/cache/apt/archives
2]double click and provide your password.
 Since you don't need ndiswrapper for your downstairs machine,do a download only.```
 sudo apt-get install -d <packages>
```

---

### Post by luckylucky on 2008-08-21
Thank you to all of you who replied with your valuable help!

I got it working!

I downloaded the deb files from the person who provided the direct links, stored on USB key, installed by double clicking them.  Then I followed the instructions on the page provided by the first person.  It didn't work at first, so I rebooted and tried again.  Mysteriously it worked the second try.

I appreciate the help... now just one more thing...

how do I mark this thread as "solved"?

---

### Post by luckylucky on 2008-08-21
I just marked this thread as "unsolved" as now the Internet is broken after doing an update on the fresh install.  Please see this other thread I just started.
[http://ubuntuforums.org/showthread.php?p=5637512](http://ubuntuforums.org/showthread.php?p=5637512)
Sorry for creating a new thread, which I started because this one was marked "solved", but just now realized that I can mark it as "unsolved".  Oh well, please accept my appologies for now having two threads on this issue.  Once resolved I will be sure to mark both "solved" and keep them linked.

---

