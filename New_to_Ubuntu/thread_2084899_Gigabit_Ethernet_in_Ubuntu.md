---
title: "Gigabit Ethernet in Ubuntu"
date: 2012-11-16
forum: New to Ubuntu
---

### Post by paulchorley on 2012-11-16
[FONT="Arial"]
Hello fellow Ubuntu-ers,

Well this is my first post to the forum, so Hi!  I hope this goes well.

I am trying to set up a Gigabit Ethernet connection between two machines; my laptop and my desktop.  So I can transfer files over NFS.

I thought I knew what was what, but alas, I can only get 100MBit.  Everything else is fine, just the actual link speed.

I am using a cable with Cat5e stamped on it.  Other pertinent information is given below.

For the (Dell W520) laptop (malachi) running Ubuntu 11.10:
[/FONT]

paulch@malachi:~> uname -a
Linux malachi 3.0.0-26-generic-pae #43-Ubuntu SMP Tue Sep 25 17:39:44 UTC 2012 i686 i686 i386 GNU/Linux

paulch@malachi:~/> lspci | grep Eth
00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)

paulch@malachi:~> sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 2
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000001 (1)
			       drv
	Link detected: yes



[FONT="Arial"]
For the (Dell Precision 380) desktop, running Ubuntu 12.10:
[/FONT]

paulch@rumfoord:~$ uname -a
Linux rumfoord 3.5.0-18-generic #29-Ubuntu SMP Fri Oct 19 10:27:31 UTC 2012 i686 i686 i686 GNU/Linux
paulch@rumfoord:~$ lspci | grep Eth
04:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
paulch@rumfoord:~$ sudo ethtool eth1
Settings for eth1:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: Symmetric
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: Symmetric Receive-only
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: off
	Supports Wake-on: g
	Wake-on: g
	Current message level: 0x000000ff (255)
			       drv probe link timer ifdown ifup rx_err tx_err
	Link detected: yes

[FONT="Arial"]
I notice that the connection has auto-negotiated a 100Mb link.  

I don't want to presume that I know too much else, so please ask if there is more I can add.

I thought this should have 'just worked' and am a little disappointed it doesn't.  I fiddled about with trying to force a 1000Mb link with ethtool, but that felt a little dirty and besides which, it didn't work.  

So, if you good people can help me a) fix my problem and b) learn how I might have solved this myself, I would be a happy Ubuntu-er.

Cheers,
Paul.
[/FONT]

---

### Post by cbanakis on 2012-11-16
The problem may be the network cable.

Everything on the computers seems to be in order.

Gigabit is technically supposed to be CAT6.

CAT5e works, but the connections/wires pretty much have to be perfect.

I networked my whole house with CAT5e, and all my devices connected at Gigabit speed.

But as the years went by, a couple of my jacks only run at 100Mbps now.

The only thing that changed between the time I had Gigabit, and now, is "time".
(Wires probably got shorts in them)

If you have another cable, I would try it.

Otherwise, you may want to try to get a CAT6

---

### Post by paulchorley on 2012-11-16
Thanks for the quick response!  I will try and 'acquire' a Cat6 cable from work and report back ..

---

### Post by audiomick on 2012-11-16
> **cbanakis said:**
> 
The only thing that changed between the time I had Gigabit, and now, is "time".
(Wires probably got shorts in them)

Just a couple of things about Cat5 cables. I doubt if they have developed shorts, as such. If they had, they wouldn't work at all. But: the cores are often solid copper and don't respond well to being rolled up. Unless it is cable material which is specifically designed to be rolled up, you can expect the cables to suffer if they are being handled. The other thing is the RJ45 connectors. I attended a seminar on Audio Networking a few years back. A chap from Yamaha had done some research into the reliability of network cables and connectors. At the time, incidentally, he was unable to find more than one or two manufacturers who were willing to say that it was alright to roll their cable up on a drum. He also found out how many plug-in cycles a normal RJ45 is guaranteed for: Two...

---

### Post by paulchorley on 2012-11-19
Got a new Cat5e cable ... problem solved!  Many, many thanks!

---

