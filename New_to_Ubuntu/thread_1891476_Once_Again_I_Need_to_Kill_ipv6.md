---
title: "Once Again I Need to Kill ipv6"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by DrMilo on 2011-12-05
The output from ip a | grep inet says, " inet 192.168.15.2/24 brd 192.168.15.255 scope global eth0". This is without a router or anything.

Am I still using ipv6?

I ask this because I have: added "net.ipv6.conf.all.disable_ipv6 = 1" to sysctl.conf, added "options ath9k nohwcrypt=1" to modprobe.d/ath9k.conf, and added "blacklist ipv6"to blacklist.conf, and I suspect that I am still running ipv6.

I have rebooted the system.

---

### Post by lemming465 on 2011-12-13
I think it's dead.  I'm not sure why you need to kill IPv6, but if were on, there would be a line starting "inet6 fe80::" and ending "/64 scope link".

---

