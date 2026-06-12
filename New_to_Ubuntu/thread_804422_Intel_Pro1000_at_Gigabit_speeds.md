---
title: "Intel Pro/1000 at Gigabit speeds ?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by drsox1899 on 2008-05-23
How can I get my Intel Pro/1000 MT to stay in 1000Mb/s mode ? 
This is in U7.10

From mii-tool I get :

eth3: negotiated 100baseTx-FD flow-control, link ok


From ethtool eth3 I get :

Supported ports: [ TP ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Advertised auto-negotiation: Yes
Speed: 1000Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 0
Transceiver: internal
Auto-negotiation: on
Supports Wake-on: umbg
Wake-on: g
Current message level: 0x00000007 (7)
Link detected: yes

What do I do to get a permanent 1000Mb/s connection ?
Do I turn off auto-negotiation ? and HowTo ?
Do I set them to AutoFullDuplex ? and HowTo ?

I have tried using :

sudo ethtool -s eth3 autoneg off speed 1000 duplex full

This changes the mii-tool output for eth3 to : negotiated flow-control, link ok
This seems to have a temporary effect only !

Thanks

---

### Post by Joeb454 on 2008-05-23
Does your network support the 1GBps speed? Your router/hub/switch will also need to be connected to your PC with a 1GBps port :)

---

### Post by apostate on 2008-05-23
> **drsox1899 said:**
> How can I get my Intel Pro/1000 MT to stay in 1000Mb/s mode ? 
This is in U7.10

From mii-tool I get :

eth3: negotiated 100baseTx-FD flow-control, link ok


From ethtool eth3 I get :

Supported ports: [ TP ]
Supported link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Supports auto-negotiation: Yes
Advertised link modes: 10baseT/Half 10baseT/Full
100baseT/Half 100baseT/Full
1000baseT/Full
Advertised auto-negotiation: Yes
Speed: 1000Mb/s
Duplex: Full
Port: Twisted Pair
PHYAD: 0
Transceiver: internal
Auto-negotiation: on
Supports Wake-on: umbg
Wake-on: g
Current message level: 0x00000007 (7)
Link detected: yes

What do I do to get a permanent 1000Mb/s connection ?
Do I turn off auto-negotiation ? and HowTo ?
Do I set them to AutoFullDuplex ? and HowTo ?

I have tried using :

sudo ethtool -s eth3 autoneg off speed 1000 duplex full

This changes the mii-tool output for eth3 to : negotiated flow-control, link ok
This seems to have a temporary effect only !

Thanks

Do not turn off auto-negotiation if you want it to work.  Gigabit speeds are only possible when the other nodes/gateway/cable-plant/etc. are also gigabit rated. If the rest of your stuff is 100baseT, it will "flow control" to match, hence negotiation. It has to be this way.

---

### Post by drsox1899 on 2008-05-23
> **Joeb454 said:**
> Does your network support the 1GBps speed? Your router/hub/switch will also need to be connected to your PC with a 1GBps port :)

All my PCs have the same NIC - Intel Pro/1000 MT.
The switches are Gigabit switches.
The cables are all Cat6
I also have 2x RAID NAS with gigabit NICs

All PCs and NASs are set to JumboFrames (9000) supported by all.

So a real mystery to me why the UBUNTU links are at FastEthernet speeds.


Now - here's something interesting :

I connected one of my NAS units directly to a PC.

In U7.10 I had a 100Mb/s connection
In U8.04 I had a 1000Mb/s connection

Since there are some other problems with U8.04 I have only one PC with U8.04 on it - the others are on U7.10.

I also got a bucketload of network errors when using U7.10 but ZERO when using U8.04.

I'll have to try putting U8.04 on another PC and seeing what the link twixt the two looks like.

---

### Post by drsox1899 on 2008-05-24
The link between 8.04 PCs works at 1000Gb/s speeds but not as well as that on WinXp.  BOOOOOOO  !!

Must find the reason why - maybe due to the driver.  The driver in U7.10 is the same as the driver in U8.04 - neither is the latest SourceForge Intel Pro/1000 driver.  So some updating is called for.

---

