---
title: "HP Pavillion dv6000 Ricoh WebCam problem !!"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by salmanmanekia on 2012-06-24
Hi All,

I am new to Linux and today installed the Ubuntu on my HP Pavillion dv6000 machine. The in built HP webcam is not working for me. I have tried to follow this forum and googled a bit for this too. I have seen then this problem is quite persitant and many people have had webcam problems with ricoh and HP. After going through all the details and trying a few of it i am still unsuccesful. Here are the relevant details. 
>> lsusb -v
 idVendor           0x05ca Ricoh Co., Ltd
 idProduct          0x1870 Webcam 1000

I have also tried [ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_i386.deb]("http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/ricoh-webcam-r5u870-firmware_0.11.6-0arakhne0_i386.deb") from [http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/](http://download.tuxfamily.org/arakhne/pool/universe/r/ricoh-webcam-r5u870/)
but to no success..

Thanks !

---

### Post by salmanmanekia on 2012-07-04
it would be great if some one can share any insights on this..i am eager to make this work !

---

### Post by gordintoronto on 2012-07-04
What version of Ubuntu? Please paste the output from a simple lsusb command. Have you installed and tried running Cheese?

---

### Post by salmanmanekia on 2012-07-04
Thanks for the reply..
1 : The ubuntu version
> root@muhammad-ubuntu:/etc/NetworkManager# lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise


2 : lsusb
> 
root@muhammad-ubuntu:/etc/NetworkManager# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:1870 Ricoh Co., Ltd Webcam 1000

3 : I have tried running cheese but it says 'no device found'

---

### Post by gordintoronto on 2012-07-04
Perhaps this will help:
[http://code.google.com/p/r5u870/](http://code.google.com/p/r5u870/)

Before you try that solution you probably need to install build-essential.

It appears that HP just installs whatever cheap webcam is available. I have an HP G62 laptop, and the webcam "just works."

BTW, I Googled:05ca:1870 ubuntu solved

---

### Post by salmanmanekia on 2012-07-05
thanks gordintoronto..It just works. The picture quality is pretty bad..but it works .. :)

---

