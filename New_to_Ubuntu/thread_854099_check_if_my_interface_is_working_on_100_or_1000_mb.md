---
title: "check if my interface is working on 100 or 1000 mbit"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by byenary on 2008-07-09
Hello,

How can i check wether my networkinterface is properly installed, it should be gigabit I started to copy 700 Gb to the server and after 12 hours it only has done 200 Gb, while he should be done by now...
Or is it maybe samba which is slowing things down.

Where should i start to look.

---

### Post by pedro_orange on 2008-07-09
Hi,

You can check what speed your network hardware interface is capable of running at by doing the following:

```
sudo ethtool eth0
```

Replace eth0 with your device eth0/eth1 etc that you want to check.

```
pedro@pedro-laptop:~$ sudo ethtool eth0
[sudo] password for pedro: 
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes

```

---

### Post by byenary on 2008-07-09
Thx, this looks all fine
root@pomerol:~# ethtool eth0
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
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

---

### Post by pedro_orange on 2008-07-09
I was trawling the buglist and found this: [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/84782](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/84782)

Also a discussion on it here: [http://ubuntuforums.org/showthread.php?t=424063&page=3](http://ubuntuforums.org/showthread.php?t=424063&page=3)

---

### Post by damis648 on 2008-07-09
Right click the network manager icon in the notification area and click "connection information".

---

### Post by mcduck on 2008-07-09
Do all the other devices in your network support 1000Mb/s network? The network speed is defined by the slowest device in the network..

---

### Post by DezSP on 2008-07-09
Ignore this post, it was rubbish.

---

