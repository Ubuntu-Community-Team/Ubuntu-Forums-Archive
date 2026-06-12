---
title: "Cannot connect Ubuntu box to modem"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by justinram22 on 2008-11-28
Hello, i've been working on this problem for the past 4 hours.  Our router just went out because of a power surge and can't afford to get a new one currently.  Here is my senario.  We have a windows desktop, and a ubuntu 8.04 hardy laptop.  When we had our router, it worked perfect, but now we are trying to take turns with the connection (sucks, but it will have to do..) and the windows box connect fine directly to the modem.  When i connect the ubuntu box the the modem, it doesn't say there is a network problem (like the 2 computers in the top right corner don't have a "!" sign by it)  and i have turned off "roaming mode" and put it to DHCP.  Now this seems to be an odd problem, because about 3 weeks ago, we had to lend out router out, so same problem, and i just put it on DHCP, restarted, and it worked fine.  Help is grealy appreciated.  I have also tried to call my ISP's Tech support, but all they say is "We do not support linux" and then after that they would not answer any general question i had... Any and All help is grealy Appreciated!

---

### Post by doas777 on 2008-11-28
cable modems don;t like being hot-swapped. everytime you change devices, I would recomend that you unplug your cable modem for 45 seconds (to clear the ram), and bring it back up before you boot the new device.

you can try to force dhcp request on the interface in question, with 

```
dhcpclient <interface>

OR

ifdown <interface>
ifup <interface>

```

see how that works,
franklin

---

