---
title: "Proxy Settings"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by nebu on 2008-11-04
[LEFT]I have ubuntu 8.04 installed.... i have put in the the network settings >>>

i put in the settings in 
1. System>Admin>Network
2. System>preferences>network proxy

the internet is working perfectly.... firefox can open google.com

but when i try to ping google.com... i get no reply....

however if i ping my proxy server.... i get a reply....

even the synaptic package manager is not able to connect to the repositories....

however the weather applet which come along with 8.04 is able to update its data....

whats wrong.... how do i fix it


i dunno if this will help...
this is what i get when i do "/sbin/ifconfig"
```

eth1      Link encap:Ethernet  HWaddr 00:a0:d1:28:ef:d8  
          inet addr:172.22.28.122  Bcast:172.22.29.255  Mask:255.255.254.0
          inet6 addr: fe80::2a0:d1ff:fe28:efd8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1848 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:763353 (745.4 KB)  TX bytes:207806 (202.9 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69900 (68.2 KB)  TX bytes:69900 (68.2 KB)


```thnx
[/LEFT]

---

### Post by wizard10000 on 2008-11-04
Can you ping the WAN side of your router?

---

### Post by rustutzman on 2008-11-04
In the proxy settings did you click the "Use this system wide" button? I'm not at my Ubuntu machine but the button is something like that.

Russ

---

### Post by nebu on 2008-11-04
**@rustutzman**
i dont seem to have anything like that on the proxy config window[B]

@wizard10000[/B]
what is the wan side of my router?? is it my gateway address.... i am able to ping my gateway address

---

### Post by Sarmacid on 2008-11-04
If you navigate with a proxy, you have to tell synaptic that. Search around the configuration and you'll find it.

---

### Post by wizard10000 on 2008-11-04
> **nebu said:**
> **@wizard10000**
what is the wan side of my router?? is it my gateway address.... i am able to ping my gateway address

Your router has two IP addresses - one that faces your network (LAN IP address) and one that faces the internet (WAN IP address).  The WAN IP address is assigned by your internet provider.

---

### Post by nebu on 2008-11-04
> **wizard10000 said:**
> Your router has two IP addresses - one that faces your network (LAN IP address) and one that faces the internet (WAN IP address).  The WAN IP address is assigned by your internet provider.
no i am not able to ping it

---

