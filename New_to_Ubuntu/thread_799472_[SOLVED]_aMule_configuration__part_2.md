---
title: "[SOLVED] aMule configuration  part 2"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Daveg4otu on 2008-05-19
After yesterday's successfull struggle I thought I'd cracked it all.

However switch on today and I find I'm back to a low ID (less than optimum  connection)

Why?............ after some poking around I find that my PC IP has changed from 192 168 0 3 to 192 168 0 2 thus requiring me to edit the Firewall rules.

Why has it changed?

There are two PCs on the router.


Is it because this PC was switched on first today? - yesterday it seems that the "other" PC was first online and received the "2" IP while this got 3. Today it's reversed.

Is there any way of ensuring that each PC always gets  the same IP (short of always switching  on in a preset order)?


It is a Netgear DG834G router

---

### Post by doug1212 on 2008-05-19
Hi,
In your router admin pages there should be a setting for reserving a particular IP address for each device connected.
Doug.

---

### Post by shadow-of-sin on 2008-05-19
You can easily setup a static ip address using the network manager in ubuntu. Just click on the network icon on the top bar, then click on "Manual Configuration". Then select: "wired connection" and click on "Properties". Now, uncheck "Roaming Mode" and set the Configuration to "Static IP Address", then type in the IP Address you want, the subnet mask and the gateway address and click ok.

---

### Post by Daveg4otu on 2008-05-21
Shadow I tried that -  no connection on those settings ...that is assuming I have used the correct details which were.....

Chosen local IP 192.168.0.2
Subnet mask  choice of 2 presumably the LAN subnet - 255.255.255.0(or should it be the ADSL port 255.255.255.255?)
 
Gateway address - again two shown in the Router config page 92.5.96.1 & 92.31.241.20

Any ideas please
BTW  ISP is AOL.

---

### Post by guilly on 2008-05-21
your gateway should be your router and not the ip provided by your ISP

check in your router settings for your gateway but it should be 192.168.0.1 mostlikely.

---

### Post by Daveg4otu on 2008-05-21
**your gateway should be your router and not the ip provided by your ISP**

Yes -realised that later - all working fine now - thanks all.

---

