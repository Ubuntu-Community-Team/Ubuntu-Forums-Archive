---
title: "No Wired Internet.."
date: 2018-01-15
forum: New to Ubuntu
---

### Post by adduds on 2018-01-15
It's been a bit for me as far as ubuntu installs but here I am again.

Connection lags and then after a while it connects but I don't have connection. 

I checked and there's no IPv4 being assigned via DHCP. Althought it is checked.

I've tried to ping 8.8.8.8

Reset networkadapter. 

I'm stumped..? Please help &#128513;

```
sirtoews@T-BUNTU:~$ ifconfig
eno1      Link encap:Ethernet  HWaddr e0:3f:49:17:15:14  
          inet6 addr: fe80::8e54:9bea:5491:60a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:30992 (30.9 KB)  TX bytes:47702 (47.7 KB)
          Interrupt:20 Memory:f7200000-f7220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2288 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:169476 (169.4 KB)  TX bytes:169476 (169.4 KB)

```

---

### Post by TheFu on 2018-01-15
Please post the output from 
```
sudo lshw -C network
```
so we can see the HW and the driver being used.

If that checks out, then we can look at other things.  DHCP is usually provided by other equipment on the network. In a home, that would be the router.  It is very possible that the router is failing. Or has a bad ethernet port or has a bad cable or ...

---

