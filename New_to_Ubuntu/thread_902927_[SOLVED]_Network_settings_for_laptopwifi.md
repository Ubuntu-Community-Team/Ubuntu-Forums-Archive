---
title: "[SOLVED] Network settings for laptop/wifi"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by stevenba on 2008-08-27
Each time I boot up ubuntu, I have to invoke the following procedure to activate my wireless connection:
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper - and then the light activates.

Furthermore, I then have to reconfigure the WPA key, as it gets trashed each time I shut down the laptop.  
Any advice as to where I can automate the procedure at startup time to activate the wifi connection and preserve the WPA key would be greatly appreciated.  I'm fairly new to Unix/Linux in general, and there seems to be so many places that this could be done, I"m not sure what the most appropriate one is...Thank you.

---

### Post by django0909 on 2008-08-27
As far as I know, adding the commands to /etc/rc.local should make them run on startup.

As for the WPA key, someone else should be able to help with that :)

--django

---

### Post by stevenba on 2008-08-27
Django, your solution fixed the wifi card initialization and the wpa key at the same time.  Very well done!  Thank you.

---

### Post by crispy_420 on 2008-08-28
Mark as solved?

---

### Post by django0909 on 2008-09-01
Sorry to bump this up to the top, I just wanted to say 'you're welcome' to the OP...

You're welcome :)

--django

---

