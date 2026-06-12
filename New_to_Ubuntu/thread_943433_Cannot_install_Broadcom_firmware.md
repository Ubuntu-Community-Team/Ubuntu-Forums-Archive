---
title: "Cannot install Broadcom firmware"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Preturbed on 2008-10-10
I've been trying to get my laptop's wireless connection going in Kubuntu using instructions provided here ( [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) ) with no luck. It worked in openSUSE yesterday but I decided the OS was too laggy.

Now I've done all the steps but can't figure out what I'm doing wrong. Kubuntu says something like "command not found."

---

### Post by shifty_powers on 2008-10-10
what version of kubuntu are you using? tbh, knetwork manager frankly sucks when it comes to broadcom chips. it has given me some proper headaches.

could you post the output of

```
sudo ifconfig && sudo iwlist scan
```

as this will let me know if it is the drivers or the network manager. (if it is, it is not actually that hard to fix :D)

they really need to do some work with knetwork manager imo. and i'm using kubuntu 8.10!

edit: have you checked the hardware drivers in applications>system>hardware drivers?

plus, 8.10 seems to have better wireless support than 8.04.1....

---

### Post by Preturbed on 2008-10-10
```

[sudo] password for isaac:
eth0      Link encap:Ethernet  HWaddr 00:03:25:20:5c:16
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe20:5c16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1870 (1.8 KB)  TX bytes:5388 (5.2 KB)
          Interrupt:10 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

isaac@Achilles:~$ sudo ifconfig && sudo iwlist scan
eth0      Link encap:Ethernet  HWaddr 00:03:25:20:5c:16
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:25ff:fe20:5c16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1870 (1.8 KB)  TX bytes:5388 (5.2 KB)
          Interrupt:10 Base address:0x3000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

```

The other thing says no proprietary drivers in use.

---

