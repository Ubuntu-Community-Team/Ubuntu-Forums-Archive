---
title: "ipw 2100 wireless card"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by mysteryMoose on 2008-09-21
:confused: i have a ipw2100 card that is recognized by my computer but not by my programs. Ethernet works just fine, but wireless is my goal. 
my boyfriend set me up on Ubuntu studio but is at a loss on this one & I am a total noob @ linux.

---

### Post by twitch2197 on 2008-09-21
you'll probably need to use ndiswrapper. it lets you use the windows drivers. search "ndiswrapper" in the forum search box and you can probably find a good walkthrough.

here's a link i found on google that might help:
[http://wiki.freespire.org/index.php/Setting_up_Ndiswrapper]("http://wiki.freespire.org/index.php/Setting_up_Ndiswrapper")

but if you need help with anything in that page, these forums are a good place to ask.

---

### Post by mysteryMoose on 2008-09-29
thanks for the link (and getting back so promptly, i havent had much time to tackle this problem this week but here i am now). it looks useful, but also that i am going to have to run freespire as my os to get wireless through that. ubuntu recognizes it. my ifconfig tells me; 

eth0      Link encap:Ethernet  HWaddr 00:0d:56:b6:b4:10  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:56ff:feb6:b410/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24365770 (23.2 MB)  TX bytes:910049 (888.7 KB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:04:23:a1:07:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Memory:faffc000-faffcfff 

eth1:avahi Link encap:Ethernet  HWaddr 00:04:23:a1:07:2a  
          inet addr:169.254.3.28  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:5 Memory:faffc000-faffcfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2548 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2548 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:146828 (143.3 KB)  TX bytes:146828 (143.3 KB)



so how can i prioritize wireless (or can i delete something to make it work?)

---

