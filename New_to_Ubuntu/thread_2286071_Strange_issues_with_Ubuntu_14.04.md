---
title: "Strange issues with Ubuntu 14.04"
date: 2015-07-09
forum: New to Ubuntu
---

### Post by onewhoknox on 2015-07-09
I'm on ubuntu 1404. I've been using it on an older laptop since around December. I woke up this morning and a notification was telling me about some kind of 'failed to parse' issue. I tried Firefox, but the connection timed out on every site I tried to visit. I tried launching some apps and some worked, but they were slower than usual [this might just be my imagination.] Every time it tried to read the app library it would suddenly stop and tell me it failed to parse. I don't even know what that means, and it was getting frustrating. I couldn't use the software center, every time I opened it, it crashed.

I left it and procrastinated on a different machine. A few hours later I think to myself 'okay, it's time to man up and fix this.' I returned to the laptop [A Lenovo Thinkpad T400, by the way] and the error notification in the top right was gone. Firefox would only connect to certain sites [I tried youtube, logical increments, and google: only logical increments would load.] I could launch and use the software center. Keep in mind that these changes happened on their own: I didn't power off the machine, I only left it sitting there.

I rebooted it. No notifications, no 'failed to parse'. But no matter what I try to connect to in firefox, I get a 'secure connection failed' message. The software center loads just fine.

Keep in mind that I've done nothing different in the past few days. The only thing I use this laptop for is browsing online and playing light games, emulators etc, so I don't know what's caused this. But the 'secure connection failed' is keeping me from using the internet.

---

### Post by sandyd on 2015-07-09
Hi, can you post the output of
```

wget https://google.com
```

Thanks!

---

### Post by onewhoknox on 2015-07-09
I did that and got this:

Resolving google.com (google.com)... failed: name or service not known.
wget: unable to resolve host address 'google.com'

---

### Post by tgalati4 on 2015-07-09
And:

```
ifconfig
```

---

### Post by onewhoknox on 2015-07-10
Not at all knowledgeable about ip and network related stuff, so I have no clue what this means. Here's what the terminal gave me:

eth0      Link encap:Ethernet  HWaddr 00:24:7e:df:e2:e6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:fc600000-fc620000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12705 (12.7 KB)  TX bytes:12705 (12.7 KB)


wlan0     Link encap:Ethernet  HWaddr 00:1e:65:38:65:64  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:65ff:fe38:6564/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:301 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25768 (25.7 KB)  TX bytes:28545 (28.5 KB)

---

### Post by onewhoknox on 2015-07-10
I reinstalled the entire OS. Every problem is fixed, except the internet. I can connect to a network, but Firefox doesn't want to connect to any websites. What now?

---

### Post by sandyd on 2015-07-10
Can you post the output of
```

route -n
ping -c10 $( ip route show | grep default | awk -F" " '{ print $3}' )

```

---

### Post by tgalati4 on 2015-07-10
And perhaps:

```
netstat -r
```

---

### Post by onewhoknox on 2015-07-10
Update: I reset the power to my router. Then, I rebooted and tried to load a webpage. I left it, and after what seemed like a VERY long time, it did load. It proceeded to load a few more: slowly. Then it returned to just timing out on everything.

I'm a little less worried now, because I was initially scared that something had gone wrong with the components of the computer itself, like my network card was screwed or something. But now I'm pretty sure it's either a problem with software, or a problem with the router [less likely because every other device is still fine.]

Anyway, here's the output.

route -n

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0







ping -c10 $( ip route show | grep default | awk -F" " '{ print $3}' )

PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
64 bytes from 192.168.0.1: icmp_seq=1 ttl=64 time=33.8 ms
64 bytes from 192.168.0.1: icmp_seq=2 ttl=64 time=3.05 ms
64 bytes from 192.168.0.1: icmp_seq=4 ttl=64 time=5.96 ms
64 bytes from 192.168.0.1: icmp_seq=5 ttl=64 time=7.86 ms
64 bytes from 192.168.0.1: icmp_seq=6 ttl=64 time=5.96 ms
64 bytes from 192.168.0.1: icmp_seq=7 ttl=64 time=3.02 ms
64 bytes from 192.168.0.1: icmp_seq=8 ttl=64 time=5.31 ms
64 bytes from 192.168.0.1: icmp_seq=9 ttl=64 time=3.04 ms
64 bytes from 192.168.0.1: icmp_seq=10 ttl=64 time=6.07 ms


--- 192.168.0.1 ping statistics ---
10 packets transmitted, 9 received, 10% packet loss, time 9008ms
rtt min/avg/max/mdev = 3.025/8.241/33.850/9.193 ms

---

