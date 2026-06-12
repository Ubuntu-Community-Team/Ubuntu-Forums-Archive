---
title: "my network is going crazy"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by akkad on 2008-09-24
i connect to the lan and the wlan successfully where the dhcp assign me with an ip and the network is accessible but the internet connectivity is strange, sometimes while i am connecting to the internet and start a new url then suddenly the connectivity disappear where the url fail, i checked the cables and the internet connection with ISP is working 100% so the problem is from my system bcuz when i open the gnome network manager and change the settings then the connection get back to work and even sometimes it doesnt work, so it is about refreshing the network settings, but what is happening exactly?? i dont know !!!!

---

### Post by beercz on 2008-09-24
What happens if you use only one connection at a time, either wireless or wired, but not both?

---

### Post by akkad on 2008-09-24
same behavior either one of them or together, actually i forgot to mention that am using virtual box and i am bridging the network, may be this will affect or something, anyway here is my interfaces output while am connection to the ethernet:

br0       Link encap:Ethernet  HWaddr 00:1c:25:1c:e9:ca  
          inet addr:172.26.2.84  Bcast:172.26.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21c:25ff:fe1c:e9ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35001 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25605595 (24.4 MB)  TX bytes:2877348 (2.7 MB)

eth0      Link encap:Ethernet  HWaddr 00:1c:25:1c:e9:ca  
          inet addr:172.26.2.84  Bcast:172.26.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21c:25ff:fe1c:e9ca/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:35250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20854 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:26303450 (25.0 MB)  TX bytes:3050153 (2.9 MB)
          Base address:0x1840 Memory:fe000000-fe020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1796 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94621 (92.4 KB)  TX bytes:94621 (92.4 KB)

tap1      Link encap:Ethernet  HWaddr 00:ff:5b:62:af:6b  
          inet6 addr: fe80::2ff:5bff:fe62:af6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11656 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:41681 (40.7 KB)  TX bytes:1566208 (1.4 MB)

tap2      Link encap:Ethernet  HWaddr 00:ff:9b:c0:9f:02  
          inet6 addr: fe80::2ff:9bff:fec0:9f02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:11623 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vbox0     Link encap:Ethernet  HWaddr 00:ff:d3:e1:2c:86  
          inet6 addr: fe80::2ff:d3ff:fee1:2c86/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:12769 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vbox1     Link encap:Ethernet  HWaddr 00:ff:4d:34:98:f4  
          inet6 addr: fe80::2ff:4dff:fe34:98f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:12769 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1c:bf:04:39:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:11970 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7525908 (7.1 MB)  TX bytes:1190876 (1.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-BF-04-39-04-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

