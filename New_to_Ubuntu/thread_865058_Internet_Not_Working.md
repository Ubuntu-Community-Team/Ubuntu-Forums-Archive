---
title: "Internet Not Working"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by cairo89 on 2008-07-20
So a little while ago I set my computer to dual boot between Vista and Ubuntu. I have both of them installed and working, except the internet on Ubuntu isn't. 

I've went to the help menu, did everything it said to do, looked on a bunch of different websites, and still haven't figured out what the problem is. So my question is, what could the problem be? 

I've also read a different post on anther board about dual booting Ubuntu, and it said the internet should pick up right away. 

I'm a complete n00b to Linux and Ubuntu right now, by the way.

Any help will be appreciated. :)

---

### Post by JagDragon on 2008-07-20
We're going to need a bit more info than that. Some things we need to know:
- Is it wired or wireless?
- How are you testing if it is working?

You'll need to open up a terminal now. Applications->Accessories->Terminal and type ```
ifconfig
``` and post the output here. Also, the output of ```
lspci | grep Network
``` would be useful to have.

---

### Post by cairo89 on 2008-07-21
I put in "ifconfig" and this is what came up:

Link encap: Ethernet   HWaddr 00: 1b:38:85:f7:cc
    UP BROADCAST MULTICAST  MTU:1500  Metric:1
    RX packets:0 errors:0 dropped:0 overruns:0 frame:0
    TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:1000
    RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
    Interrupt:17 Base address:0x1000

    Link encap:Local Loopback
    inet addr:127.0.0.1 Mask:255.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOP BACK RUNNING MTU:16436 Metric:1
    RX packets:1816 errors:0 dropped:0 overruns:0 frame:0
    TX packets:1816 errors:0 dropped:0 overruns:0 carrier:0
    collisions:0 txqueuelen:0
    RX bytes:103728 (101.2 KB) TX bytes:103728 (101.2 KB)
_______________________________________________________________________________________

When I put in lspci | grep Network:

01.00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev02)
-----------------------------------------------------------------------------------------

I have no clue what any of that means, hopefully someone will. =S

I'm testing to see if it works, just by opening Firefox and trying to go to an Ubuntu start page, and it says "can not find server" 

and it's wireless.

---

