---
title: "how to enable/disable wireless in command line"
date: 2010-03-07
forum: Programming Talk
---

### Post by bhuvi on 2010-03-07
in ubuntu by right clicking the network manager applet and by toggling enable wireless i can switch on/off wireless but how to do it using command line.

---

### Post by not_a_phd on 2010-03-07
I think the command you seek is:

```
ifconfig ra0 down
```

to bring it back up:

```
ifconfig ra0 up
```

---

### Post by matchett808 on 2010-03-07
remember to correctly replace ra0 with your interface (ath0 wlan0 eth0 eth1 etc etc etc!)

---

### Post by bhuvi on 2010-03-08
replacing it with eth1 worked thanks

---

### Post by ngrieb on 2011-09-05
How can I run this in a script at boot and shutdown (as it seems to require a sudo permission)? I am having eth0 problems when I boot, and I suspect it is because of the enabled eth0 connection at shutdown (I am running x86 11.04).

Thanks in advance.

---

### Post by fdrake on 2011-09-05
> **ngrieb said:**
> How can I run this in a script at boot and shutdown (as it seems to require a sudo permission)? I am having eth0 problems when I boot, and I suspect it is because of the enabled eth0 connection at shutdown (I am running x86 11.04).

Thanks in advance.

this should help:
[http://ubuntuforums.org/showthread.php?t=1838337](http://ubuntuforums.org/showthread.php?t=1838337)

---

### Post by Jake5 on 2012-03-03
What if this is not working, running lubuntu 11.10.

---

