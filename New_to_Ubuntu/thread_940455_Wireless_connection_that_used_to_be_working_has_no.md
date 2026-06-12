---
title: "Wireless connection that used to be working has now spit the dummy"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Anonono on 2008-10-07
I've been using a wireless connections to a router for internet in Ubuntu ever since I installed it, and now it won't connect.
I tried deleting it, and making a new one, but that doesn't do a thing.
Something that is probably completely related (But I'll mentioned anyway) is that my Ubuntu partition failed a check. I restarted, and skipped it. The wireless was working fine (This was before it pooped), but then it dropped out.
I've tried restarting the router, but it still didn't work, so I booted into Windows, and it worked fine.

Help.

---

### Post by Anonono on 2008-10-07
Anyone?

---

### Post by pastalavista on 2008-10-07
post output ```
ifconfig
```

---

### Post by Anonono on 2008-10-07
> **pastalavista said:**
> post output ```
ifconfig
```

```
eth0      Link encap:Ethernet  HWaddr 00:16:ec:ea:32:a7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1066 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53300 (52.0 KB)  TX bytes:53300 (52.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:50:63:c5:f8  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:fe63:c5f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:66 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48615 (47.4 KB)  TX bytes:11998 (11.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-11-50-63-C5-F8-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by Anonono on 2008-10-07
Anyone?!

---

### Post by pastalavista on 2008-10-07
It appears wlan0, which is my wireless connection, is working ok. It's getting some traffic. Can you reach the router with the browser? I don't have any knowledge of wmaster0. Is that a USB adapter?

---

