---
title: "Automatic eth0 connection won't use my interface settings"
date: 2011-09-29
forum: New to Ubuntu
---

### Post by AskTell on 2011-09-29
I'm running Ubuntu desktop 10.04 LTS

Whenever i restart my server or lose my connection Ubuntu automatically connects with dhcp settings and obtains an automatic ip instead of the static ip i've setup in /etc/network/interfaces

auto lo
iface lo inet loopback
iface eth0 inet static
address 192.168.1.104
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.1.1


I can ifdown/ifup eth0 to obtain a static ip.  I tried changing the Auto eth0 settings by right clicking the up/down arrow at the top right of my screen and selecting  "Edit Connections"  selecting auto eth0 and editing it options under the ipv4 settings changing it from dhcp to manual and filling in the required ip address, netmask, and gateway. this connection didn't work. After that i figured I'd try removing Auto eth0 it to see if a new auto eth0 would be created with my current interfaces settings, this did not work. I tried disabling the automatic connection option under "Edit Connections" and this prevented me from obtaining a connection even when i tried ifdown/ifup leading me to re-enable the automatic connection option fixing the newly created problem.

This is the first of many many questions...

---

### Post by dwasifar on 2011-09-29
Manual settings in /etc/network/interfaces are superseded by the settings in Network Manager.  You have to either set your static IP using Network Manager, or disable Network Manager to use /etc/network/interfaces settings.

When you were "clicking the up/down arrow" you were in the Network Manager settings tool.  I don't know why your settings changes didn't work there, but it often has to do with altering the wrong interface, or not selecting the interface to be available to all users, or not selecting it to be active on startup.

If you prefer to configure your interfaces manually by editing the config files, as it seems you do, just *sudo apt-get remove network-manager* and all will be as you expect.

---

### Post by The Cog on 2011-09-30
I thought that network-manager would ignore interfaces that were defined in /etc/network/interfaces. Is my memory wrong there?

I think the posted /etc/network/interfaces is missing the line> auto eth0, which may be why it's not working.

Here's an example from [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/) (found in google search)
```
# An example ethernet card setup: (broadcast and gateway are optional)
#
# auto eth0
# iface eth0 inet static
#     address 192.168.0.42
#     network 192.168.0.0
#     netmask 255.255.255.0
#     broadcast 192.168.0.255
#     gateway 192.168.0.1
```:

---

### Post by drdos2006 on 2011-09-30
auto lo
iface lo inet loopback
iface eth0 inet static
address 192.168.1.104
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.1.1

I would have thought that the network should be 192.168.1.0 not 192.168.0.0  and that the broadcast should be 192.168.1.255 not 192.168.0.255.

regards

---

### Post by The Cog on 2011-09-30
> **drdos2006 said:**
> auto lo
iface lo inet loopback
iface eth0 inet static
address 192.168.1.104
netmask 255.255.255.0
network 192.168.0.0
broadcast 192.168.0.255
gateway 192.168.1.1

I would have thought that the network should be 192.168.1.0 not 192.168.0.0  and that the broadcast should be 192.168.1.255 not 192.168.0.255.

regards
Doh! I didn't even look at the numbers. You are right - as posted, they don't make sense. I still think it probably needs an auto eth0 as well though.

---

### Post by AskTell on 2011-10-04
Okay so using dhcp in /etc/network/interfaces automaticly filled in the required nameserver entries in /etc/resolv.conf then i turned it back to static and everything worked just fine, what setting am i missing to do this automaticly with an empty resolv.conf using static settings? should i repost this in a new thread since a fix has been established for this one and a new question arose?

---

### Post by The Cog on 2011-10-05
My understanding is that if you use static network configuration, then putting the nameserver details in /etc/resolv.conf is a necessary part of that static configuration.

---

### Post by AskTell on 2011-10-05
How would i discover the name servers if dhcp didn't work or had been disabled?

---

### Post by The Cog on 2011-10-05
The same way as you get an IP address, subnet mask and default gateway - ask the network administrator. All these things have to be decided by the administrator.

---

### Post by AskTell on 2011-10-05
I found the dns entries in my Linksys router under status and I don't have an admin. :( just me. :biggrin:

---

### Post by The Cog on 2011-10-06
Ah, right. In that case, your ISP is effectively the network admn. I've had 4 ISPs over the years, and every one of them has given me the required details as part of their introductory information. I suppose that may not be so common these days, with ISPs that simply assume that you will use a router that gets the info from the PPP session setup between router router and the ISP. Especially if the ISP provides the router - it just happens that I've never used an ISP that provides its own modem/router.

---

### Post by AskTell on 2011-10-09
Well all my question(s) were answered so I'm marking this solved

---

