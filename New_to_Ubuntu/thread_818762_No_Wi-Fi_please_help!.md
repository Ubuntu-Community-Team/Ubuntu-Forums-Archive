---
title: "No Wi-Fi please help!"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by EnergySamus on 2008-06-04
Hi!
So I recently had Ubuntu 7.10 installed, and I got my wi-fi drivers working by going to restricted drivers and enabling my Broadcom 43xx wi-fi card. I installed 8.04 and I now have to use a Lan cable to connect to my router! How do I install these wi-fi drivers for my Ubuntu Pc? Any help would be apreciated, thanks!


EnergySamus

P.S. While we are at it, can someone tell me how to install adobe flash?:lolflag:

---

### Post by tj111 on 2008-06-04
Have you gone to System->Administration->Hardware Drivers and made sure that the driver is enabled?

---

### Post by InfinityCircuit on 2008-06-04
In the new kernels bcm43xx is replaced by b43.

```
sudo apt-get install b43-fwcutter flashplugin-nonfree
```

---

### Post by EnergySamus on 2008-06-04
> **InfinityCircuit said:**
> In the new kernels bcm43xx is replaced by b43.

```
sudo apt-get install b43-fwcutter flashplugin-nonfree
```

When I type that in it says "couldn't find package b43-fwcutter

EnergySamus

---

