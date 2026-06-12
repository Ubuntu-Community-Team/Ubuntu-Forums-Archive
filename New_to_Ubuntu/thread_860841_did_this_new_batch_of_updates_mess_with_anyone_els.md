---
title: "did this new batch of updates mess with anyone else's wireless?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2008-07-16
i updated my laptop today (IIRC it was all linux kernel stuff, headers and modules and such) and after the reboot it prompted me for after updating i can't get online.

wicd shows it's connected to my AP, and when i hit the wireless switch on my laptop the signal drops to zero. it shoots back up to 79 or 80% when i reenable my wireless.

i ruled out anything further up the chain than my laptop, because i am typing this on my desktop that is connected over wireless to my AP in the same manner; and i have no issues.

i have an intel IPW3945 wireless card, is anyone having similar issues with this chip?

---

### Post by jbrown96 on 2008-07-17
the interface might be deactivated for some reason. See if it is listed in ifconfig. In a terminal, ```
ifconfig
``` It will probably be listed as wlan0 or eth1. If it is not listed try ```
sudo ifconfig wlan0 up
``` If it complains about the interface not existing, try eth1 instead of wlan0. You can also try to install a newer version of the driver, but it will require internet access. You need to enable the Backports repository in Synaptic or /etc/apt/sources.lst . Then install linux-backports-modules-hardy-generic in Synaptic or in a terminal ```
sudo apt-get update
``` then ```
sudo apt-get install linux-backports-modules-hardy-generic
```

---

