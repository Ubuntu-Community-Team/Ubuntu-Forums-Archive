---
title: "Acer Aspire One D270 with Ubuntu 12.04 LTS no wifi"
date: 2012-11-13
forum: New to Ubuntu
---

### Post by gatesdrovme2it on 2012-11-13
It just stopped today.  I have a D-link DIR-412 wireless router with a D-link 3.75G aircard m/n DWM-156.  All lights on the router are green, as is the single LED on the aircard.  I hae totally deleted my connection, which is WPA/WPA2 Personal.  I then added the connection back again manually.  I re-entered the password and triple-checked it for accuracy.  All I ever see in the upper right corner beside the speaker and volume indicator is that darn inerted outline that is an empty cone shape.

I feel angry!  But maybe someone can help?

---

### Post by ercherramon on 2012-11-13
Your netbook has Broadcom BCM4313 chip? If so, try to connect from the ethernet and install the proprietary driver for that card Wireless:

```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

That'd better configured with your wi-fi.

---

