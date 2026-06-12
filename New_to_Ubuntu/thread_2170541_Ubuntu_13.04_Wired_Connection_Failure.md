---
title: "Ubuntu 13.04 Wired Connection Failure"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by aehainsworth on 2013-08-26
So everything was running smoothly last night. I was going to bed, so I turned the PC off as usual. No biggie.

Shortly after I woke up, I booted up the PC and it became immediately obvious that the wired connection wasn't working anymore. I checked the router and it was fine. So I switched over to wireless and bam, we have a connection again.

What could be the problem with the wired connection?

---

### Post by bkline on 2013-08-26
Try another cable.

---

### Post by aehainsworth on 2013-08-26
Well, thank you for your helpful suggestion, but that was pretty much the first thing I did. It's actually the third time I replaced the cable and the second time was a little more than a month ago.

---

### Post by r_avital on 2013-08-27
If you go to system-settings>network, any useful info there?  If the ethernet (wired) connection exists, can you look at options?  Is the ip4 setting set to DHCP?  If the ethernet connection is not there, can you create a new one?  These are things I would try, just to see if the system is even aware of a physical wired connection to the router.

Also, instead of replacing cables, does the act of disconnecting/1 or 2 minute wait/reconnecting the cable have any effect?

---

### Post by aehainsworth on 2013-09-20
> **r_avital said:**
> If you go to system-settings>network, any useful info there?  If the ethernet (wired) connection exists, can you look at options?  Is the ip4 setting set to DHCP?  If the ethernet connection is not there, can you create a new one?  These are things I would try, just to see if the system is even aware of a physical wired connection to the router.

Also, instead of replacing cables, does the act of disconnecting/1 or 2 minute wait/reconnecting the cable have any effect?

It's set to DHCP. I've never turned it off before. However, I'll have to check on the wired connection's information the next time it doesn't work, and I'll try the physical disconnect/reconnect suggestion too.

Actually, it happens again now and then. I'd say maybe every 5-7 boot-ups or so. So it's not a rare problem for me, and it usually recognizes the wired connection on the next restart.

---

### Post by varunendra on 2013-09-21
Might be interesting to see what card and driver you are using, as well as the effective settings in use. Please show us the outputs of -
```
lshw -C network
ifconfig -a
nm-tool
sudo ethtool eth0
```
..assuming the interface is named "eth0". If it is something else, change it accordingly. You may need to install ethtool first (sudo apt-get install ethtool).

---

