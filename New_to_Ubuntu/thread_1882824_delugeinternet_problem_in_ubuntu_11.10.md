---
title: "deluge/internet problem in ubuntu 11.10"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by jawer on 2011-11-18
hai all,

1. i install ubuntu 10.04, deluge work fine for a while. after install 11.10 deluge wont work anymore and keep say no incoming connection
2. internet connection also buggy and unstable

i use >> 11.10, modem>> W3400V innacom

try to find solution for 3 days now. nothing fixed
:confused::confused::confused::confused:

a.
```
lspci | grep Wireless
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```
b.ifconfig
```
eth0      Link encap:Ethernet  HWaddr bc:ae:c5:10:f7:18  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:47 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2046 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:178971 (178.9 KB)  TX bytes:178971 (178.9 KB)

wlan0     Link encap:Ethernet  HWaddr 48:5d:60:74:c4:24  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3079279 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3999783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2321223435 (2.3 GB)  TX bytes:1345952555 (1.3 GB)

```

---

