---
title: "adding route in Routing Table"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Buessa on 2008-06-07
Would any expert Help in this?!! command for Adding route in the "Routing Table" of Linux ubuntu Ver 8.x. Thanx.
Samad

---

### Post by Monicker on 2008-06-07
> **Buessa said:**
> Would any expert Help in this?!! command for Adding route in the "Routing Table" of Linux ubuntu Ver 8.x. Thanx.
Samad

The basic syntax is pretty straightforward.

```

sudo route add -net 10.0.0.0 netmask 255.255.255.0 gw 192.168.1.1
```

..for example.  "man route" for more details and options.


A few details about what you want to do exactly would be helpful.

---

### Post by Andrewsha on 2008-06-09
Hello!

I have notebook at work on LAN. Internet and  local net are OK automatically after installing Ubuntu.

But I must to have access to some "host". I can do manually at console:
```
route add -host 10.1.xxx.xx gw 10.2.y.yy eth0
```
After this everything is OK. But when I had lost connection then I need manually run comand again:
```
route add -host 10.1.xxx.xx gw 10.2.y.yy eth0
```

Also I need run comand after reboot PC.

Read somewhere that I should add something at /etc/network/interfaces Here is my /etc/network/interfaces :
```
auto lo
iface lo inet loopback
```

That's all! Nothing else. I tried to write something in it but unsuccessfully.

**The question**: what should i write to /etc/network/interfaces or somewhere else to have my route always up?

Result of "route" on my PC before manually route add:
```
~$ route
&#1058;&#1072;&#1073;&#1083;&#1080;&#1094;&#1072; &#1084;&#1072;&#1088;&#1096;&#1091;&#1090;&#1080;&#1079;&#1072;&#1094;&#1080;&#1080; &#1103;&#1076;&#1088;&#1072; &#1087;&#1088;&#1086;&#1090;&#1086;&#1082;&#1086;&#1083;&#1072; IP
Destination Gateway Genmask Flags Metric Ref Use Iface
10.2.0.0        *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         10.2.1.1        0.0.0.0         UG    0      0        0 eth0
```


Thanks for advance!

---

### Post by Monicker on 2008-06-09
Andrewsha

Personally, I would just add the route command you use to /etc/rc.local, which will cause it to be executed every time the system boots up.

---

### Post by Andrewsha on 2008-06-10
OK, but what about lost connection? Will it re-run?

---

