---
title: "USB tethering not working"
date: 2018-10-25
forum: New to Ubuntu
---

### Post by zdbxcfb97 on 2018-10-25
i'm currently using ubuntu 14.04.5. the USB tethering in ubuntu is not working. it cannot tethered for internet. i am it is not my phone problem because it works fine in my windows 10. (i dualboot my laptop)
```
woodz@woodz:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 4c:cc:6a:7e:ca:eb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4504 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:442918 (442.9 KB)  TX bytes:442918 (442.9 KB)


vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.226.1  Bcast:192.168.226.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.171.1  Bcast:192.168.171.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr b8:81:98:80:39:9b  
          inet addr:192.168.43.94  Bcast:192.168.43.255  Mask:255.255.255.0
          inet6 addr: fe80::ba81:98ff:fe80:399b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:164488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64964 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:197680279 (197.6 MB)  TX bytes:12294699 (12.2 MB)
```

---

