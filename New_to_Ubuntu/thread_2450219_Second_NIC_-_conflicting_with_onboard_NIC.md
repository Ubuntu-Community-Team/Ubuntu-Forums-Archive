---
title: "Second NIC - conflicting with onboard NIC"
date: 2020-09-09
forum: New to Ubuntu
---

### Post by borderbeebs on 2020-09-09
Hi, complete Newbie to the world of Linux and Ubuntu.  Put in a second boot drive for Ubuntu into a workstation so I could play around and try and learn Docker, and running into a NIC issue.

There is an onboard NIC on the computer.  For some audio networking on the windows drive, I require a 2nd NIC in the system.  On the Windows 10 side I plugged in the PCIe NIC, turned on the computer and the system saw the NIC and everything works great.

When I boot up the Ubuntu drive, the system can see both NICs and their respective MACs, but if they're both plugged into their respective switches (one internal only, one with access to the outside internet) neither of them work.
The PCIe NIC says its connected, but doesn't pass anything, and the onboard NIC just says 'connecting' but never locks, and doesn't give me internet access.  

Strangely, if I unplug the onboard NIC and disable it, I can plug the PCIe NIC into the switch that accesses the outside world, and Ubuntu tells me that I'm actually using the on-board NIC to do so, even though that NIC doesn't even have a Cat5 cable plugged into it.

Very strange.  I'm thinking a port/driver conflict of some kind as the NICs just really seem be getting confused with each other.  I honestly don't know enough about Linux/Ubuntu to know where to even begin.  I could always just unplug the PCIe NIC when I need to use Ubuntu, and plug it back in when I'm on the Windows side, but I'd rather just fix the problem as I'll eventually need both NICs to work on the Linux side.  

Help?

---

### Post by TheFu on 2020-09-09
I cannot help if either are wifi.  I don't do wifi.

I don't know how to do network troubleshooting for a newbie, but if you are comfortable with the CLI interface, we can figure some things out.  If you are clear about what you want, please say that providing exact details and the setup should be fast if the cards are working.
For each card, please say, 
IP, netmask, gateway, DNS servers and search order. If you have a DHCP server on the respective networks, we can probably get that working too.

The easiest solution would be to have 1 card configured, the other unconfigured and using dhcp.

---

### Post by borderbeebs on 2020-09-09
No wifi involved.  Both are physical RJ45/Cat5 connections.

I'll get an ifconfig from the Terminal with the details listed here in a bit.  I'm trying to have my onboard NIC that connects to the internet be a dynamic DHCP address, but the PCIe NIC that connects to the internal only network have a static IP assigned to it.

---

### Post by borderbeebs on 2020-09-09
And....just sorted out my mistake.

I set the static IP on the wrong NIC.  I compared the MAC addresses to the actual MAC on the PCIe card and I had the wrong one configured to DHCP and static respectively.

I switched those around, and everything is now working as it should. 

Sigh.

Sometimes you just have to try and explain it, and you figure it out I guess.

---

### Post by TheFu on 2020-09-09
> **borderbeebs said:**
> Sometimes you just have to try and explain it, and you figure it out I guess.

I completely understand!  The act of trying to explain something in detail for someone else often helps solidify knowledge and forces doubt-checking stuff.  Mistakes are uncovered that way, for me as well.

Can't say how many times I'd be planning to post a question here, then change my hat to what the person answering will need to know to help.  
[LIST]
[*]Have I checked the log files for errors?
[*]What is the configuration? Please post the config files.
[*]What have I already tried? Did I google?
[*]Did I try to simplify the setup already?  Get the parts working separately before trying to get something complex working.
[/LIST]

That list, is usually the beginnings of me discovering where I made a simple mistake.

Happy you found the issue.  90% of the time here, we don't have the answer, but our questions lead to the OP finding the answer on their own. Make sense, because we don't have access to the system and every individual is biases due to our own backgrounds and history.

---

