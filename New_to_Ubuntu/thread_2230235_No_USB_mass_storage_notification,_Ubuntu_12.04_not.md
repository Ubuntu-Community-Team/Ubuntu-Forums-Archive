---
title: "No USB mass storage notification, Ubuntu 12.04 not able to mount galaxy tab 2"
date: 2014-06-18
forum: New to Ubuntu
---

### Post by gaxydroid on 2014-06-18
Hi Experts,


Hi have Samsung Galaxy Tab 2 10.1 wifi only tablet with:
Model Number: GT-P5110
Android Version: 4.0.3
Kernel Version: 3.0.8-365113-user
                      se.infra@SEP-62 # 1
Build Number: IML74K.P5110XXALD6


When I am connecting my tablet with my Ubuntu 12.04 Dell laptop, it is not getting connected with the laptop.  However the battery starts charging after the connection.  The tablet is also not giving USB mass storage/camera notification while earlier I was able to connect to PC and device was getting recognized.
I checked in Wireless and network > more and couldn't find any USB utility/setting.  I even tried factory reset the tablet but it didn't help.
Other USB android devices are being mounted to my PC without any issue.  I tried installing mtp-tools but, no luck.


Please guide me if something needs to be changed at tablet or some change in the laptop.

---

### Post by 3rdalbum on 2014-06-18
Hi, Ubuntu 12.04 can't mount Android 4 phones. You should either upgrade to 14.04, or run an FTP server on your phone and connect it to the computer's WiFi network (or run the FTP server and turn on tethering).

Ubuntu 14.04 can mount Android 4.x phones out-of-the-box with no troubles.

---

### Post by zemega on 2014-06-18
Ubuntu 12.04 can mount MTP devices after manual/PPA installation of MTP related stuffs. But I do agree, you should upgrade to 14.04.

---

### Post by ajgreeny on 2014-06-18
If you must keep 12.04 have a good look at the thread at [http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702) which gives a lot of info which may help you.

---

