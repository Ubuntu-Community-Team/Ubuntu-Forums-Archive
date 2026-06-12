---
title: "trying (and failing) to use PPPoE"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by coladict on 2008-11-23
Hi there.
Ultimate noob (to all things linux) here, trying to configure my internet connection on Ubuntu 8.04.1
I had to come boot back to Windows a few times to download the pppoe package and look-up some old threads to see if I can get it going, but still no dice. What I usually do in Windows is disable the TCP/IP for that ethernet adapter (because of whatever I can't connect when it's enabled there) and create a PPPoE connection to the service "profi-max" with the user name "coladict8823" and my password accordingly. I tried setting up a connection under Ubuntu using pppoeconf, but... well I don't know what's wrong with it.
here's some of what you'd probably ask me for.
```
root@katz-desktop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:44:7e:79  
          inet6 addr: fe80::215:f2ff:fe44:7e79/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4705 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:370085 (361.4 KB)  TX bytes:10496 (10.2 KB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:e0:4c:03:e6:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xa000 

eth1:avahi Link encap:Ethernet  HWaddr 00:e0:4c:03:e6:45  
          inet addr:169.254.6.115  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:506 errors:0 dropped:0 overruns:0 frame:0
          TX packets:506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:26620 (25.9 KB)  TX bytes:26620 (25.9 KB)

root@katz-desktop:~# pon dsl-provider
Plugin rp-pppoe.so loaded.
root@katz-desktop:~# plog
Nov 23 20:38:33 katz-desktop pppd[6258]: CHAP authentication failed
Nov 23 20:38:33 katz-desktop pppd[6258]: Connection terminated.
Nov 23 20:38:40 katz-desktop pppd[6407]: Plugin rp-pppoe.so loaded.
Nov 23 20:38:40 katz-desktop pppd[6409]: pppd 2.4.4 started by root, uid 0
Nov 23 20:38:40 katz-desktop pppd[6409]: PPP session is 379
Nov 23 20:38:40 katz-desktop pppd[6409]: Using interface ppp0
Nov 23 20:38:40 katz-desktop pppd[6409]: Connect: ppp0 <--> eth0
Nov 23 20:38:43 katz-desktop pppd[6409]: CHAP authentication failed: 8$M-ZM-7prM-mM-7^F
Nov 23 20:38:43 katz-desktop pppd[6409]: CHAP authentication failed
Nov 23 20:38:43 katz-desktop pppd[6409]: Connection terminated.
root@katz-desktop:~# 

```
eth1 is the currently unplugged second ethernet adapter I used to use to share my internet with my PS3. 
You can see some packets received in eth0 because there's some other computers on the network also connected the same way.
I took a look at that dsl-provider file and I didn't see the password pppoeconf asked me for, neither did I see a field for the service name.

---

