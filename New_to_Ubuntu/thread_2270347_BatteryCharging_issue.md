---
title: "Battery/Charging issue"
date: 2015-03-22
forum: New to Ubuntu
---

### Post by Madan_Bhandari on 2015-03-22
Hi Friends, I am new to Ubuntu. I am facing battery problem with my Laptop (Dell Vostro 2520/i5/4GB/500GB). My Laptop's battery drains very fast (really very fast as compared to windows 8.1) and other than it get fully charged very fast as compared to Windows 8.1. So what's the problem here ?

I am using dual boot ubuntu 14.04 LTS and Windows 8.1.

Please Help me to fix this issue.

Thanks.

---

### Post by dino99 on 2015-03-22
maybe it needs a full discharge before recharging it. But ubuntu is known to use more power than windows. in fact, all depends on how the powersaving settings (into bios) are set, and if you also use a lot of 3D and/or sliding animation (which can be turned off)

---

### Post by mc4man on 2015-03-22
Boot up, log in & wait for 1.5 - 2 min. 
Then run these 2 commands in a terminal (ctrl+alt+t to open one) & post results of both
```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_driver
```
```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

---

### Post by Madan_Bhandari on 2016-01-22
what does this command ??

---

