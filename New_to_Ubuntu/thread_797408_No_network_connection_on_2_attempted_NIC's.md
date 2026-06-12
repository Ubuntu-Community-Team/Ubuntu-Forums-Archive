---
title: "No network connection on 2 attempted NIC's"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by Porwah on 2008-05-17
I think I'm losing it.  I've been trying to get a network connection on my dual boot WinXP / Ubuntu box for 4-5 days now.  WinXP side has worked fine.  Ubuntu has never connected.

I first tried using the on board lan -- a Realtek RTL8100B chip.  No luck after countless attempts and tweaking of settings.

I decided I might try a addon card.  I put in a DLink NIC and I still don't have a connection.

I think there's something fundamentally wrong with my config settings.

My my experience with WinXP and OS X, I would set the network to DHCP, add in DNS's, subnet mask and gateway (router IP).

In hardy, I go to the Network Admin and select DHCP there.  I saw a spot to add the DNS's.  shouldn't I have to add the Subnet mask and Gateway too? I've run dhclient on both cards and it broadcasts out the DHCPDISCOVER but that's it.  

I tried doing a static IP under the Network admin too.  At least that shows me options to set the Subnet Mask and Gateway.  But I still can't ping my router doing that. (And obviously don't have any connection.)

I really can't think these just happen to be two bad NIC's.  I think there's something fundamentally wrong with how I'm configuring my settings.

Can anyone tell me anything I might be missing here? It might be obvious to you but something's eluding me.  I'm a Linux newbie but not unfamiliar with a command line and editing text files.

---

### Post by Monicker on 2008-05-17
Usually dhcp supplies the dns settings, along with gateway and subnet mask for the client to use.

Try running the following command

```
ethtool eth0
```


You may have to change the interface name to reflect what is actually on your computer.  Look at the line for "link detected".  Does it say yes, or no?

I would also check the output of dmesg, to see if it shows any problems bringing up the network card.

---

### Post by zvacet on 2008-05-17
On the top panel on the right side you will see two monitors icon.It is network manager applet.Clicl on it and you will see manual config>network settings(properties)>select your modem (just click on it but not tick box)>properties>select dhcp>DNS tab> if you have router leave address you find there and add your nameservers>connection tab>now tick your modem and window will pop up with message changing newtork interfaces.When it is done type in terminal 

```
pppoeconf
```

---

### Post by Porwah on 2008-05-17
Thanks for your replies.

So I have the Link Detected Yes line in my ethtool output.  That's encouraging.

I dumped the dmesg output too.  I have no idea what all the stuff means though.

@zvacet: my network settings is pretty much all as you said already.  pppoeconf looks like it's for DSL.  I have cable.  

Here's what I get from dhclient:
```
There is already a pid file /var/run/dhclient.pid with pid 5704
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:20:ed:28:f1:86
Sending on   LPF/eth0/00:20:ed:28:f1:86
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Here's my interfaces:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

I've attached these as well as the dmesg output too.  I hope this means something to someone who can shed a little light on this for me.  It's certainly a pain rebooting to WinXP to post!

---

### Post by Porwah on 2008-05-18
bump!

---

### Post by volkswagner on 2008-05-18
What do you get for

```
ifconfig
```

---

### Post by mbarak on 2008-05-18
try restarting your router (and cable modem)(that is - turning it off and on not reset all the settings) and unplug all the Ethernet cables (between your router and computer and modem) when it turns on plug the cables back in. I've had a problem like this before - it seemed everything SHOULD have worked but for some reason didn't want to (this was with XP and with Ubuntu) perhaps that will work
***make sure to first go into your network settings and make sure "enable roaming mode" is checked so that network-manager can manage your connection and make your life easier :)

---

### Post by Porwah on 2008-05-18
@volkswagner: thanks for the reply.  ifconfig output is below...

@mbarak: thanks for the reply.  Just tried power cycling router, switch on Ubuntu side (I'm dual booting with XP).  No luck.  Yet it  does work fine in XP.  Are you serious about the roaming thing? I don't know what that is, but I interpretted that as more for wireless stuff.  I'm strictly wired for this machine.

I've spent 10+ hrs now on this issue.  I'm seaming together a debug process.  Maybe someone can confirm this process is logical and might see something in my results that I'm missing/overlooking.

1) lspci seems to see my onboard LAN chip.  Here are the results of that:

```
00:13.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

2) and ethtool seems to see it too.  Results: 

```
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

So can I assume Ubuntu has correctly loaded a driver for my hardware? And further, the ethtool results show a link detected. It sees the network -- if that means anything.

A little more on that... from my router I can see an entry in a client table for the box.  It shows the same MAC address in ifconfig (shown later.)  There's no IP for the entry in the client table though.

3) On to network admin and settings.  Output of cat /etc/network/interfaces is: 

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

The network admin dialog (under System / Administration / Network) shows DHCP.  I've added my two DNS servers on the appropriate tab too.

4) I ran dhclient on eth0.  Grr..  Just saw the results of that command didn't save to a file.  But the results were the same as the prior post.  Here's the results of that earlier attempt.

```
There is already a pid file /var/run/dhclient.pid with pid 5704
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:20:ed:28:f1:86
Sending on   LPF/eth0/00:20:ed:28:f1:86
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

So it looks like it's a no go there.  On the router, I check the logs and it sees a DHCP request offer in from my box, and it says an offer with an IP has gone out.  Hmm... so what's going on?

5) My ifconfig results still show no IP:

```
eth0      Link encap:Ethernet  HWaddr 00:20:ed:28:f1:86  
          inet6 addr: fe80::220:edff:fe28:f186/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xcc00 

```

Looking at that... should I have the inet6 line? I'm supposed to see a line with an IPv4 IP, right???

6) I cannot ping my router.  And my router cannot ping my box.  REsults of pinging my router: 

```
PING 192.168.11.1 (192.168.11.1) 56(84) bytes of data.
From 169.254.8.213 icmp_seq=2 Destination Host Unreachable
From 169.254.8.213 icmp_seq=3 Destination Host Unreachable
From 169.254.8.213 icmp_seq=4 Destination Host Unreachable

--- 192.168.11.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2999ms
, pipe 3

```


Question on this: what is the 169.254.8.213??? Where is that coming from? I don't recognize that IP from anything?

I'm pretty much out of ideas on this one so if anyone can help it would be greatly appreciated.

---

### Post by volkswagner on 2008-05-18
> Question on this: what is the 169.254.8.213

This is and address issued by the pc.  This happens when DHCP fails to issue an address via the router.

I am curious.  I expected to to eth0 and eth1.  Your onboard is not recognised at all?  Or is your pci card not recognised?

Have you tried to create a static address from the information while logged into windows.  Use the same ip, subnet, etc.?

Did you have a working lan via the live cd?

---

### Post by Porwah on 2008-05-18
> **volkswagner said:**
> I am curious.  I expected to to eth0 and eth1.  Your onboard is not recognised at all?  Or is your pci card not recognised?

I removed an addon card.  I installed that as a temporary measure to see if it would have any different results.  So I am only trying to get the onboard LAN chip working at this point.

I do not know how to tell if they're recognized.  I was kind of asking that in my last post.  Do the results in (1) and (2) from lspci and ethtool mean that my card is recognized?

> **volkswagner said:**
> Have you tried to create a static address from the information while logged into windows.  Use the same ip, subnet, etc.?

I've tried a static IP in Ubuntu using the appropriate subnet mask, dns, and gateway.  I have to set those in WinXP and OS X (I have a mac on the network too.)  They work fine with those settings.  Ubuntu has the same results as with DHCP.  I cannot ping my router or other boxes on the network when I set up a static IP manually.

One note on that: I don't set the IP to what DHCP does on the WinXP side. I just have used some other random number that I know is in the range I allow on the router.  I don't think that's a big deal.

> **volkswagner said:**
> Did you have a working lan via the live cd?

I just tried the Live CD again.  I do not have a working lan with it.  I ran ifconfig and AFAI can tell it's the same results as my installed setup with dhcp.

I hope all this is clear.  If not, please let me know.

So I'm still at a loss here...

---

### Post by Porwah on 2008-05-18
Some further debugging information:

I used the 8.04 Live CD in another WinXP box and that got on the network automatically.  It received an IP, and all the tabs under the Network Admin dialog were set with info I would think appropriate.  I got on the internet fine.

And since I can get an IP and get on the internet fine under XP on the box in question, this got me thinking it was a hardware issue again.

So I installed a DLink NIC again.  I used this same card in a third box that had only Ubuntu on it.  To my memory, I didn't do anything and the box was on the internet fine.  It recognized the card fine.  That Ubuntu box was 7.10.

Yet, in my dual boot box in question, this card also fails to get an IP from my router.  This is just nuts.

Restating some facts:
- another box gets on network fine with live cd
- box in question does not connect with live cd
- box in question dual boots and XP side gets on network fine
- on board and separate network card both fail to get IP under Ubuntu on dual boot machine
- separate network card was used successfully on another machine with solely Ubuntu 7.10 installed on it.  Card was recognized on install.

Can anyone see something I'm missing? Sorry to keep posting.  This is driving me nuts.

---

### Post by volkswagner on 2008-05-18
To complete your debug you need to run 7.10 live cd on the dual boot machine with you network card installed.  This will tell you if it an 8.04 issue w/your cards.

---

### Post by Porwah on 2008-05-20
I didn't get to try this right away, but sadly:

7.10 and 8.04 live cd's don't get a connection with the addon NIC on the dual boot machine.

and reconfirmed 7.10 and 8.04 live cd's DO get a connection with the same addon NIC on a single boot machine.

I'd consider buying a new NIC for all this trouble, but this card is listed as working out of the box in 7.10.  It's a D-Link DFE-530TX.  And the same is true for the onboard LAN chip too (RTL8100B).

---

### Post by volkswagner on 2008-05-21
I would try to disable onboard lan in bios.  Use the addon card to see if you can get it to work.

You may also want to post in hardware or networking.

---

