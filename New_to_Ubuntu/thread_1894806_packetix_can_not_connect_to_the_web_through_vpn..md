---
title: "packetix can not connect to the web through vpn."
date: 2011-12-13
forum: New to Ubuntu
---

### Post by naoyuki on 2011-12-13
I  set up the packetix vpn client in ubuntu 11.10, and i could set up vpnclient and set vpncmd up. but, i could not succeed to  connect to the internet through the VPN .

i knew i connected to the interneti only n normal routing because i can not see youtube ,facebook, here in china.
packetix works perfect with windows OS.

i don't know how to adjust routing table.
someone help me.
```
root@naoyuki:/home/naoyuki/vpnclient# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:32:bb:3f  
          inet addr:192.168.133.207  Bcast:192.168.133.255  Mask:255.255.255.128
          inet6 addr: fe80::20a:e4ff:fe32:bb3f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1015489 errors:0 dropped:0 overruns:0 frame:0
          TX packets:694528 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:324716633 (324.7 MB)  TX bytes:65803264 (65.8 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17798 (17.7 KB)  TX bytes:17798 (17.7 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:192.168.3.87  P-t-P:192.168.3.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1400  Metric:1
          RX packets:815977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:535839 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:246384769 (246.3 MB)  TX bytes:26725607 (26.7 MB)

vpn_0     Link encap:Ethernet  HWaddr 00:ac:1a:bb:94:6f  
          inet addr:10.11.39.223  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2ac:1aff:febb:946f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1454522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:120576206 (120.5 MB)  TX bytes:1959724 (1.9 MB)

```

---

