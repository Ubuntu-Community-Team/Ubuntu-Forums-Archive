---
title: "Very Slow wireless network"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Vic20 on 2008-10-16
Hi all. 

experienced ms-dos to windows user here. 

Have just installed Ubuntu 8.1 Beta on a Dell P4 Machine.

Quite liking Ubuntu but I am having problems with the wireless network being very slow.

The Realtek RT2500 54G wireless is intermittantly connecting and ony at 1Mb/sec where in windows it is usually at 36Mb/sec or higher. When it does connect, it asks for the WPA password most times.

Download speed is around 30KB per sec at most where in Windows it is over 300KB/sec

A ping to my Linksys Router in terminal with no-one else accesing the network gives greatly varying results...

64 bytes from 192.168.1.1: icmp_seq=67 ttl=64 time=2.17 ms
64 bytes from 192.168.1.1: icmp_seq=68 ttl=64 time=2.17 ms
64 bytes from 192.168.1.1: icmp_seq=69 ttl=64 time=56.5 ms
64 bytes from 192.168.1.1: icmp_seq=70 ttl=64 time=3.14 ms
64 bytes from 192.168.1.1: icmp_seq=71 ttl=64 time=423 ms
64 bytes from 192.168.1.1: icmp_seq=72 ttl=64 time=2.12 ms
64 bytes from 192.168.1.1: icmp_seq=73 ttl=64 time=2.15 ms
64 bytes from 192.168.1.1: icmp_seq=74 ttl=64 time=2.12 ms

please help

Vic

---

### Post by hyper_ch on 2008-10-16
I have the same issue with my wireless.

run

```

sudo iwconfig wlan0 rate 54M && sudo /etc/init.d/networking restart

```

Run iwconfig first to see whether your wifi device is also set as wlan0

And also add yourself to the bug report: [https://bugs.launchpad.net/ubuntu/+bug/282053](https://bugs.launchpad.net/ubuntu/+bug/282053)

---

### Post by Vic20 on 2008-10-16
> **hyper_ch said:**
> I have the same issue with my wireless.

run

```

sudo iwconfig wlan0 rate 54M && sudo /etc/init.d/networking restart

```



That did the trick, many thanks! 

Pings are much more consistent too now at around 1.5ms, Downloads still aren't quite as quick as in windows though.

Is this a permanent change?

---

### Post by Vic20 on 2008-10-16
Spoke too soon, although the wireless connection speed is now at max, the connection still keeps disconnecting at intervals   and requesting the WPA password on reconnect.

The signal strength indicated also varies from 47-88%  over several minutes.

Vic

---

### Post by hyper_ch on 2008-10-17
you might want to try WICD as network manager then...

---

### Post by Vic20 on 2008-10-17
Wicd??

---

### Post by nothingspecial on 2008-10-17
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

