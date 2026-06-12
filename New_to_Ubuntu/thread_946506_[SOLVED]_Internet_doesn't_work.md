---
title: "[SOLVED] Internet doesn't work"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Crayboff on 2008-10-13
I recently installed Firestarter thinking it'd be a decent firewall, but it sort of messed things up so I uninstalled it completely and deleted it from Session. However, now I cannot get onto the internet anymore via Hardy Heron. I have FIOS for internet and it was working fine before, it is temperamental on my Vista but works fine after some bashing it into the table a few times.

---

### Post by superprash2003 on 2008-10-13
well first thing that could be done is flushing your iptables cause firestarter may have messed it up [http://prash-babu.blogspot.com/2008/10/how-to-flush-or-remove-all-iptables.html](http://prash-babu.blogspot.com/2008/10/how-to-flush-or-remove-all-iptables.html)

---

### Post by Crayboff on 2008-10-13
thanks. I did
Thanks everyone who helped me. This is what I ran:


```
sudo iptables -F
sudo iptables -P INPUT ACCEPT
sudo iptables -P OUTPUT ACCEPT
sudo iptables -P FORWARD ACCEPT
sudo iptables -X

sudo apt-get purge firestarter
```

also here are what I have for the $ifconfig:
**Before sudo iptables:**
```
eth0      Link encap:Ethernet  HWaddr 00:1d:09:a4:76:9d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7000 (6.8 KB)  TX bytes:7000 (6.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:8c:31:74:6e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1535 (1.4 KB)  TX bytes:5405 (5.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-8C-31-74-6E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
[B]
After sudo iptables:[/B]
```

eth0      Link encap:Ethernet  HWaddr 00:1d:09:a4:76:9d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7000 (6.8 KB)  TX bytes:7000 (6.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:8c:31:74:6e  
          inet6 addr: fe80::21e:8cff:fe31:746e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1847 (1.8 KB)  TX bytes:6717 (6.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-8C-31-74-6E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

