---
title: "How to disable touchpad."
date: 2016-10-07
forum: New to Ubuntu
---

### Post by devnatu on 2016-10-07
> **dtom2 said:**
> Hi,

thank you all for your replies. Finally i solved the problem  looking around the net. The problem lies with the touchpad driver most  probably. As soon as it was blacklisted installation continued just  fine. 

so you have to blacklist the driver by modprobe.blacklist=i2c_hid.


Hi 

I am struggling a lot with the boot problems, can you please let me know how did you disable the touchpad.

thanks 

Dev

---

### Post by Bucky Ball on 2016-10-07
*Post moved to own thread.*

Welcome. Have you tried Applications> Settings> Mouse and Touchpad and disable the touchpad? 

The way it was solved on the thread you originally posted on is posted in the OP's last post on that thread.

---

