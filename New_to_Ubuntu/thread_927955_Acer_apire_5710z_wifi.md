---
title: "Acer apire 5710z wifi"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Bukarts on 2008-09-23
The main problem is that I already tried out everything (I think so, and hope i did everything correctly).   I can't connect to the wi fi  it shows the bar at the bottom but it is empty  all the time, and I cant check the box in hardware drivers, by the way it shows that driver is in use without checked box.  Can someone help me STEP by STEP! Thanx in advice! :):lolflag:

---

### Post by roquefilipe on 2008-09-23
[I see]("http://laptoping.com/acer-aspire-5710z-ubuntu-linux.html") that notebook is available with Ubuntu pre-installed. Was your notebook one of those?

Anyway, you say you tried everything, but what exactly? 

Also you need to tell us what is exactly you wifi card, so run this on the terminal and post the result
```
lshw -C network
```

If you have already tried to use ndiswrapper, have you tried to follow this guide in the Networking & Wireless section: [Comprehensive ndiswrapper troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847")

---

### Post by paul101 on 2008-09-23
are you using the 64bit version of ubuntu??


i had probs with the x64 version with my aspire 5920, works great with the 32 bit

---

