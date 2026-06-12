---
title: "Need an iptables rule"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by BGFG on 2008-08-22
Anyone out there familiar with iptables ?
I'm currently going through Linux 2.4 packet filtering HOWTO by Rusty Russel.
Reading up and getting along slowly, basically I'd like to create a Filtering/State rule that only accepts packets from connections initiated by my machine.

Any help appreciated, hope some network gurus are browsing today...

---

### Post by rockerphil on 2008-08-22
iptables can be pretty daunting to the new Linux user, so my best advice is to use a GUI frontend to configure your iptables, my personal favorite is firestarter. it's very easy to configure your iptables with and once configured can simply be closed out. you can install it with this code,

```
sudo apt-get install firestarter
```

hope this helps,


Phil

---

### Post by Majorix on 2008-08-22
> **rockerphil said:**
> iptables can be pretty daunting to the new Linux user, so my best advice is to use a GUI frontend to configure your iptables, my personal favorite is firestarter. it's very easy to configure your iptables with and once configured can simply be closed out. you can install it with this code,

```
sudo apt-get install firestarter
```

hope this helps,


Phil

+1. No need to write your own rules when you can use GUI to do it much easier/faster.

---

### Post by BGFG on 2008-08-22
Thanks Guys,
Crap. I already use firestarter, you see my problem is that i believe that my ISP is throttling me. So i am looking to find a way to sieve out junk packets but if i'm already doing this sufficiently then that means the scoundrels simply have me sharing an inadequate pipe with other users.

I'll still persevere with iptables though. Something new to learn.

Is firestarter still being developed ?

---

### Post by JKyleOKC on 2008-08-22
Here are the two rules I use to accept any packet in an already-established connection. However I don't think they will filter out the forged RST packets.

-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

-A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT 

You might be able to use a modification of these to REJECT or DROP any incoming RST packets, though; I think the only bad effect of dropping a valid RST packet at the end of a connection is that the connection will go into TIME WAIT state and time out eventually, thus possibly slowing your throughput slightly...

Incidentally I have both rules because the box on which they run also serves as my router. The INPUT chain handles packets addressed to the box itself and the FORWARD chain handles the NAT packets for the rest of my LAN.

Learning iptables can be frustrating, but once learned you'll be amazed at the power it gives you.

---

### Post by rockerphil on 2008-08-22
i know with Firestarter you can enable ICMP filtering and pick and choose what kind of packets you want allowed, i personally uncheck all boxes, which of course makes it to where my box wont allow, ping or pong requests, timestanmping, MS Traceroute, Traceroute, unrechable, adress masking, redirection, and source quenching, and it seems to work well for me. i also block broadcasts from both internal and external networks, along with blocking traffic from reserved addresses on public networks, all of this done with Firestarter, saving me the hassle of writing my own iptable rules. hope this information helps,

Phil

edit: if you're looking for a bit more configuration/customization capabilities you may want to give guarddog a shot, it takes a bit more time to configure, but it's a very powerfull GUI frontend to the iptables

---

### Post by bodhi.zazen on 2008-08-22
Firestarter is outdated and no longer maintained. Ubuntu now uses UFW:

[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

If you want a gui, take a look at gufw :

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

### Post by BGFG on 2008-08-22
So outdated that it's no longer viable ? At All ?

Thanks for that Gufw link :)

---

### Post by bodhi.zazen on 2008-08-22
Well, there are a number of issues with firestarter.

The two biggest I have are :

1. It runs as root.

2. More important, it tends to fail if you have anything more then the most basic of firewall needs. If you start bridging your network card or using NAT or using VMWare or writing rules in iptables, firestarter can (and often does) fail.

Firestarter was last updated in January 2005

---

### Post by BGFG on 2008-08-22
As of now I think my needs are pretty basic. Just need to rid my bandwith of junk.
As for your second point :) I'm not there yet... I think i'll give firestarter up until Intrepid, then switch over to Gufw.

One question. Since iptables is a kernel module. I assume Gufw has significantly less processor overhead than Firestarter with ICMP turned on ?

Edit: Apparently i need to have both Traceroute's turned on.

---

