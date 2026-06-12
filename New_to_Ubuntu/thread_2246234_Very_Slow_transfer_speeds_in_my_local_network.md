---
title: "Very Slow transfer speeds in my local network"
date: 2014-09-29
forum: New to Ubuntu
---

### Post by Angel_Perez on 2014-09-29
Hello Guys,

Im a newbie with Ubuntu, i just installed last night in a i5 16gb computer at home, im been experiencing a couple of issues like freezing, partitions, etc but the one that really frustrate me is why this extremely slow speeds at home. 

The computer have gigabit card, my NAS have gigabit card, my switch is gigabit and im trying to copy pictures from my NAS to the computer and the speed right now is 1mb per second.

Any idea? any setting in ubuntu? I did this before with a windows computer and never had this issue.

Thanks in advance for any help

---

### Post by Michael_McKenney on 2014-09-29
[https://help.ubuntu.com/10.04/serverguide/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/network-configuration.html)

---

### Post by nerdtron on 2014-09-29
> [https://help.ubuntu.com/10.04/server...iguration.html]("https://help.ubuntu.com/10.04/serverguide/network-configuration.html")
This is outdated and the OP is not setting up a server.

> The computer have gigabit card, my NAS have gigabit card, my switch is  gigabit and im trying to copy pictures from my NAS to the computer and  the speed right now is 1mb per second.

How do you transfer files from Ubuntu to NAS? And what is this NAS? How is it mounted in Ubunu?
Let's see also if your gigabit card is in gigabit mode in Ubuntu.
Run in the terminal (if your network link is not eth0, then change the command):
```
ethtool eth0
```

If the above command did not work of ethtool is not installed, try:
```
dmesg | grep eth0
```

---

### Post by Michael_McKenney on 2014-09-29
Do you have a up to date site for Network tweaks on a server.  I am running server grade hardware.  The NIC seems very slow.

---

### Post by Angel_Perez on 2014-09-29
> **nerdtron said:**
> This is outdated and the OP is not setting up a server.



How do you transfer files from Ubuntu to NAS? And what is this NAS? How is it mounted in Ubunu?
Let's see also if your gigabit card is in gigabit mode in Ubuntu.
Run in the terminal (if your network link is not eth0, then change the command):
```
ethtool eth0
```

If the above command did not work of ethtool is not installed, try:
```
dmesg | grep eth0
```

Hi, Thanks for the help,

I have a "Go Flex 3tb NAS gigabit connected to the switch

I just browse the NAS in the network, double click and enter user and password, then copy the files and try to paste in my desktop and the transfer start.

Is automatically mounted to Ubuntu in the "Network Area in "Places"

This is the info i got when run the "ethtool eth0"  :


[CODE][Settings for eth0:
 Supported ports: [ TP MII ]
 Supported link modes:   10baseT/Half 10baseT/Full 
                         100baseT/Half 100baseT/Full 
                         1000baseT/Half 1000baseT/Full 
 Supported pause frame use: No
 Supports auto-negotiation: Yes
 Advertised link modes:  10baseT/Half 10baseT/Full 
                         100baseT/Half 100baseT/Full 
                         1000baseT/Half 1000baseT/Full 
 Advertised pause frame use: Symmetric Receive-only
 Advertised auto-negotiation: Yes
 Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                      100baseT/Half 100baseT/Full 
                                      1000baseT/Full 
 Link partner advertised pause frame use: Symmetric
 Link partner advertised auto-negotiation: Yes
 Speed: 1000Mb/s
 Duplex: Full
 Port: MII
 PHYAD: 0
 Transceiver: internal
 Auto-negotiation: on
Cannot get wake-on-lan settings: Operation not permitted
 Current message level: 0x00000033 (51)
          drv probe ifdown ifup
 Link detected: yes/CODE]

---

