---
title: "Wireless Connection Problems"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by deton8whore on 2008-07-25
When I open up the network manager, there is no option for wireless networks. And I have a router set up already.

I have the HP Pavilion tx 1000, unsure about wireless card info.

---

### Post by bobnutfield on 2008-07-25
Open a terminal and type:

> lspci

This will tell you what wireless chipset you have (it should be close to the bottom of the listing, it usually is).

Post this information back to enable us to better tell you how to set it up.

Bob

---

### Post by deton8whore on 2008-07-25
> **bobnutfield said:**
> Open a terminal and type:



This will tell you what wireless chipset you have (it should be close to the bottom of the listing, it usually is).

Post this information back to enable us to better tell you how to set it up.

Bob

Is there any way to find this out from Vista? (I am on right now)

---

### Post by bobnutfield on 2008-07-26
Yes, you can find this information in the control panel, system, devices.  Look at network it will tell you what wireless card you have.  Or, if you have one, load up the live Ubuntu CD and you can run the above command in a terminal.

Bob

---

