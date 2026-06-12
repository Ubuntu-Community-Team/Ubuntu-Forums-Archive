---
title: "Selecting which NIC to use"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by bigmonmulgrew on 2008-10-11
I have 2 network cards plugged in to my PC at the min.
1 is a WPN311
the other is a 
WG121
Both netgear
I had the WPN setup and working but i think its on the way out.
I want them both connected for now but I cant find out how to turn the WPN off and use the WG instead.
The WPN is PCI and I want it plugged in for windows at the min.

I'm using WICD if it makes any difference.

---

### Post by superprash2003 on 2008-10-11
find out which interface corresponds to which card.. if the WPN corresponds to eth0 then type ifdown eth0 to disable it.

---

### Post by bigmonmulgrew on 2008-10-12
could you be a little more specific please.
I'm a bit vague on the networking in ubuntu

---

### Post by superprash2003 on 2008-10-13
in your terminal type ifconfig .. then you should see a list of interfaces.like eth0,eth1 or wlan0 etc etc.since you have 2 network cards plugged in.. you should see 2 interfaces(excluding lo).. so you need to find out which interface corresponds to which network card.. you can do that by simply plugging in a network connection in one of the cards.. the interface which shows connected is the interface which corresponds to the connected network card.. so find out which interface corresponds to WPN . say for example it is eth0. then type ifdown eth0 to disable it

---

