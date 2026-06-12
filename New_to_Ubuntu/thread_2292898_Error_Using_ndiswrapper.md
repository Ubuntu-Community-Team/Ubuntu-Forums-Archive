---
title: "Error Using ndiswrapper"
date: 2015-08-31
forum: New to Ubuntu
---

### Post by Daniel_Jackson on 2015-08-31
While trying to install my driver I get an error.
Using 
sudo ndiswrapper -i bcm43xx32.inf 
I get 
Couldn't open bcm43xx33.inf: no such file or directory at /usr/sbin/ndiswrapper-1.9 line 219. 

How do I fix this problem?

---

### Post by sandyd on 2015-08-31
Hi, what device are you trying to install a driver for? You may not have to use ndiswrapper

That being said, you have to point ndiswrapper to an existing inf file for the driver in order for it to work.

---

### Post by Daniel_Jackson on 2015-08-31
> **sandyd said:**
> Hi, what device are you trying to install a driver for? You may not have to use ndiswrapper

That being said, you have to point ndiswrapper to an existing inf file for the driver in order for it to work.

Its a broadcom device, ive figured it out (kind of) by doing
Cd ~/Downloads 
And then -i works. Except I had the .inf file present but forgot to add in the .sys file. Now, the driver is installed but not properly. Do you know how I can uninstall the driver?
(Im very new to ubuntu)

---

### Post by monkeybrain20122 on 2015-08-31
Which broadcom card is that? Most of them don't need ndiswrapper nowadays. 
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
[http://askubuntu.com/questions/509465/the-old-broadcom-43xx-beast-strikes-again-14-04-32bit](http://askubuntu.com/questions/509465/the-old-broadcom-43xx-beast-strikes-again-14-04-32bit)

---

### Post by Daniel_Jackson on 2015-08-31
> **monkeybrain20122 said:**
> Which broadcom card is that? Most of them don't need ndiswrapper nowadays. 
[http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)
[http://askubuntu.com/questions/509465/the-old-broadcom-43xx-beast-strikes-again-14-04-32bit](http://askubuntu.com/questions/509465/the-old-broadcom-43xx-beast-strikes-again-14-04-32bit)
Netgear n300 wireless adapter. Everywhere ive read, everyone says that the only way to get this one to work is with ndiswrapper

---

### Post by Daniel_Jackson on 2015-09-01
I figured it out! I just ran the actual program 
sudo ndisgtk
And was able to unistall the faulty driver, then reinstall the correct way!
I now have working wifi!

---

