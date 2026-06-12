---
title: "Can’t connect to secured wifi router"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by olimb on 2008-10-29
Using Ubuntu 8.4 I am able to connect to an unsecured wifi router, but when I try to connect to a secured router using the correct password the connection attempt times out.
Hardware Information
Broadcom Corporation BCOM4306 802.11 b/g Wireless LAN Controller (rev 03)
Subsystem Linksys WPC54G 

The Linksys driver was installed with ndiswrapper and ndisgtk

---

### Post by scizzo on 2008-10-29
Have you checked in /var/log/messages, /var/log/syslog and /var/log/auth.log of what is failing if it is the authentication or the like?

---

### Post by roger_1960 on 2008-10-29
Hi

In the 'networking and wireless' forum archives there seem to be several threads on the subject of WPA authentication with the 4306.  If this is your problem, perhaps search there a little

[http://ubuntuforums.org/showthread.php?t=669842](http://ubuntuforums.org/showthread.php?t=669842)

[http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

If you are having trouble with WPA, then you are not alone.  Is it your own router?  Can you reconfigure it to use WEP instead?

---

### Post by kreggz on 2008-10-29
so you connect to a wireless lan that is unsecured and then that connects to a router?

---

