---
title: "Internet connection has ceased to work."
date: 2008-07-10
forum: New to Ubuntu
---

### Post by Wrensky on 2008-07-10
Hey all. After much deliberation, experimenting around with Wubi, and finally having a new burner to back up files with, I'm finally an Ubuntu user as of yesterday. Unfortunately, I'm on the live CD right now, as my actual installation has been cut off from the net as of a half an hour ago.

It was working fantastically till then, but while I was still connected, suddenly everything I tried to download through the Add/Remove Applications manager was giving me errors. It said it couldn't get a lock (I believe, I might be remembering wrong), and suggested that perhaps another package manager was running, which to my knowledge was not so.

So I, having had to deal with windows for a long time, I naively restarted had my computer restart in hopes that it would clear up whatever was going on. Unfortunately, when I reached my desktop again, no packages would download at all, firefox wasn't able to load pages, my buddy list wasn't reachable, and all around effects of not having a connection.

I'm on Hardy Heron, 64 version to be exact, on broadband, my service provider is AT&T (in California if that matters), and have a Linksys WRT54G wireless router, but the actual computer connection is wired. Wireless connection is going strong, if my Wii is any indication.

Given that it's only my main install that is cut off, I'm hoping this is simply a mistake I made that I can fix and learn from, I'm just not sure where to start.

I DID have some trouble while trying to install VMWare (Which I succeeded with thanks to a thread in the virtualization forum), so maybe that might've caused it.

Any help in advance is extremely appreciated, I just want to get things up and running again, and am happy to provide any further needed information. :(

---

### Post by DezSP on 2008-07-10
Could you run ifconfig from a terminal and post the results here. Thanks.

---

### Post by Wrensky on 2008-07-10
Sure thing.

> eth0      Link encap:Ethernet  HWaddr 00:16:17:eb:ef:26  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:feeb:ef26/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9147149 (8.7 MB)  TX bytes:1097297 (1.0 MB)
          Interrupt:23 Base address:0xe800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:171200 (167.1 KB)  TX bytes:171200 (167.1 KB)

---

### Post by DezSP on 2008-07-10
That seems fine... You might want to check your router isn't playing any silly games. You can try shutting down your PC and the router, leaving them both off for 1 minute then powering it all up again -- that'll release the DHCP and force your PC to pick up another address... Also check you don't have any firewall running (iptables or firestarter, etc.) and blocking your connections, though unless you set that up yourself it seems unlikely.

---

### Post by Wrensky on 2008-07-10
Just got back on the liveCD from doing that, and nada, still nothing.

Also, no firewalls involved either.

---

### Post by DezSP on 2008-07-11
Well that kinda stumps me. All I could suggest is running dpkg-reconfigure on network-manager et al (I don't know what the networking packages names are off-hand) as root and see if that fixes it.

---

### Post by kevmitch on 2008-07-11
Can you get through to your router?
```
ping 192.168.2.1
```

---

