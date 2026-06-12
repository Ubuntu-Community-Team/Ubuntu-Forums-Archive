---
title: "Download apps once install many times"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by everlearnin on 2012-11-29
Hi 
Is there a way to download an app once then put it on a usb drive and transport it to other ubuntu installations. I have to pay for every mb of internet I use so I am not fond of the idea of downloading an app more than once. 

Thanks

---

### Post by zombifier25 on 2012-11-29
The downloaded installers are in /var/cache/apt/archives . Simply copy the .deb files you want to install to the other machines, and open them with Ubuntu Software Center to install them (not really recommended, since USC is really slow), or run this command in the terminal to install all the .deb files (make sure you're in the same directory):
```
sudo dpkg -i *.deb
```

NOTE: Make sure you collect all the necessary packages, or some dependencies may not be satisfied.

---

### Post by ryankidman on 2012-11-29
Buy genuine apps they can be installed many times

---

### Post by deadflowr on 2012-11-29
> **ryankidman said:**
> Buy genuine apps they can be installed many times

Huh?

You can install AptonCD, it's in the software center.
It'll let you either burn your packages to a cd/dvd, or let you create an .iso image which you can load onto a pendrive.

[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---

