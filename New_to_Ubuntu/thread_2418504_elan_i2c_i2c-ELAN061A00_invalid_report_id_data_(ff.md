---
title: "elan_i2c i2c-ELAN061A:00: invalid report id data (ff) in kernel logs"
date: 2019-05-07
forum: New to Ubuntu
---

### Post by kibrislihuso on 2019-05-07
Hi, 

I installed lubuntu 19.04 and did kernel update  from 5.0.13 to 5.1.0-050100-generic, to make my touchpad usable and i am getting "elan_i2c i2c-ELAN061A:00: invalid report id data (ff)" this error in kernel logs. My touchpad is working but writing too much logs when i am using it. I think there is a bug here.

My laptop is Lenovo-V130-15IGM 


Regards.

---

### Post by Xian on 2019-05-07
You may want to blacklist the elan_i2c  module. 

To do this edit your /etc/modprobe.d/blacklist.conf file. 

Add the following lines: 
```
# Do not load the elan_i2c module 
blacklist elan_i2c
```

---

### Post by kibrislihuso on 2019-05-08
Hi,

When i add this line into blacklist.conf my touchpad is not working. I want to use my touchpad.


Regards.

---

### Post by Xian on 2019-05-08
> **kibrislihuso said:**
> 
When i add this line into blacklist.conf my touchpad is not working. I want to use my touchpad.


Okay that's a good thing. If your syslog is getting spammed by this warning message but all is working then how far you want to chase this down is up to you. Start by searching through some already reported instances on the bug tracker and apply what you believe to be useful.

For example: [https://bugs.launchpad.net/ubuntu/+source/linux-hwe-edge/+bug/1735677](https://bugs.launchpad.net/ubuntu/+source/linux-hwe-edge/+bug/1735677)

---

### Post by kibrislihuso on 2019-05-10
thanks for your support. I set a hourly cron which clears kern.log and syslog. But i am open for another solutions.

Regards.

---

