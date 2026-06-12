---
title: "reliance netconnect plus problem in ubuntu 11.10"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by ARUN RAHUL on 2012-05-22
Hi,,
I am new to linux.I started with ubuntu
I recently installed ubuntu 11.10 on my dell vostro 1540
I successfully connected reliance netconnect zte modem in it.
I checked the "connect automatically" checkbox while connecting.
But when I restarted the system it tries to connect .....and shows the message "Network disconnected"...
Though I manually connected it is not connecting and is just showing the message "network disconnected"
For the first time it worked well but is not working well afterwards when i restarted the system.
So i switched to 10.10 in which modem is working well...
How to solve it in 11.10

---

### Post by fantab on 2012-05-22
**[See This]("http://ubuntuforums.org/showthread.php?t=1578325")**.

Check if "usb-modeswitch is installed, if not then install it.  But since you say it worked for sometime then it is probably installed. 

Edit your connection: PPP Settings- Configure Methods-  _*UNCHECK*_ MSCHAP & MSCHAP v2

Contact your service provider if all else fails...

---

### Post by ARUN RAHUL on 2012-05-22
ok thank u

---

