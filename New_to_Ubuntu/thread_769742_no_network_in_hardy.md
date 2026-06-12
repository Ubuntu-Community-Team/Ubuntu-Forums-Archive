---
title: "no network in hardy"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by wabbalee on 2008-04-26
Hello,

I have just installed hardy on one of my machines and everything seems to work fine but one thing: i cannot connect to the network/internet.

when i look in gutsy's network tools and select the eth0 card i can see that protocols IPv4 and IPv6 are installed

when checking the same in hardy i only see IPv6 installed

Does anybody recognize this and found a way to install IPv4 in hardy?

I think once I have IPv4 protocol in hardy i will have connection again.

thanks in advance
Ron

---

### Post by tamoneya on 2008-04-26
post the output of ```
ifconfig
```

---

### Post by wabbalee on 2008-04-27
root@laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:96:3e:46  
          inet6 addr: fe80::216:36ff:fe96:3e46/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1598 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:79900 (78.0 KB)  TX bytes:79900 (78.0 KB)

root@laptop:~#

---

