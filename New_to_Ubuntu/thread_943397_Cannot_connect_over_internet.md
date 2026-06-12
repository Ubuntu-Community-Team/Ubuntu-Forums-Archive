---
title: "Cannot connect over internet"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Konstabel on 2008-10-10
I have a working ssh connection to my home machine. It does have an ip that (is supposed) can be seen from outside.

I have cable internet and is setup as follows:
Cable->TV/Telephone/Internet splitter->Modem->Router->Machine

What can I try and do to fix this problem?

---

### Post by hyper_ch on 2008-10-10
you need to forward port 22 from the router to your machine. For that it's also adviced to set your machine to a static IP in the lan.

---

### Post by Konstabel on 2008-10-10
Then I must be mistaken, my "router" does not have an interface to do port forwarding. All it does is to split the incoming internet signal to my wi-fi router and home pc (by cable).

---

### Post by hyper_ch on 2008-10-10
konstabel model is that router?

---

### Post by Konstabel on 2008-10-10
I believe it is a D-link. The exact model I don't know, and will only be able to check when I get back home. Will post it then.

A more accurate description would be a switch not a router. Just checked the difference.

---

### Post by hyper_ch on 2008-10-10
I'm pretty sure it's a router and not a switch.

---

### Post by Konstabel on 2008-10-10
I checked my system and see attached picture for layout:

---

### Post by hyper_ch on 2008-10-10
I can't find that device.. but you have an "internet modem" there... so check if there's a firewall on it.

---

### Post by Konstabel on 2008-10-10
I assume the device you cannot find is the DES-1500D? I miss typed, it should be DES-1005D.

Concerning the firewall on the modem, it was issued by the service provider so I'll have to check with them. Can't find any documentation.

---

### Post by hyper_ch on 2008-10-10
the d-link is a switch...
how did you determine your external ip and what does
```

iconfig

```
return?

---

### Post by Konstabel on 2008-10-10
I got my address with the ifconfig command. This is what it returns

[I]eth0      Link encap:Ethernet  HWaddr 00:00:1a:1a:39:ec
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr 00:00:1a:1a:39:eb
          inet addr:84.195.189.30  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::200:1aff:fe1a:39eb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1756584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2927892 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:133298529 (127.1 MB)  TX bytes:4016433788 (3.7 GB)
          Interrupt:17

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7753 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1566329 (1.4 MB)  TX bytes:1566329 (1.4 MB)
[/I]

The IP address I get for the Wi-Fi router is very similar also 84.195.x.x

---

### Post by hyper_ch on 2008-10-10
and what do you get when you go to [http://www.whatismyip.com](http://www.whatismyip.com) ?

---

### Post by Konstabel on 2008-10-10
I get the same address as that of my Wi-Fi router (I am working from my XP laptop). Therefore I assume the Ubuntu machine IP should be able to be seen from outside.

I did a lynx browse to whatismyip and found the same address as with ifconfig

---

### Post by hyper_ch on 2008-10-10
that is the case... so I guess you got the firewall up... by default it does not block any ports... did you install some firewall tools?

---

### Post by Konstabel on 2008-10-10
No, no firewall tools installed.

---

### Post by virtualsolutions002 on 2008-10-10
If your internet is not working properly or you are not able to connect to the internet it might be solved by asking the service provider. They can give you a better solution for your problem.



Albert

[Crystal Meth](http://www.crystalrecovery.com)

---

### Post by virtualsolutions002 on 2008-10-10
If your internet is not working properly or you are not able to connect to the internet it might be solved by asking the service provider. They can give you a better solution for your problem.


Albert 



[Crystal Meth](http://www.crystalrecovery.com)

---

### Post by Konstabel on 2008-10-10
I am not having trouble connecting to the internet, but connecting from the internet to my home server.

---

### Post by hyper_ch on 2008-10-10
well, could still be firewall on the server.

---

### Post by Konstabel on 2008-10-10
Does Herring come with a firewall installed? How can I check if there is indeed a firewall?

---

### Post by hyper_ch on 2008-10-11
Heron comes with a firewall but by default it's set to let everything pass...

---

