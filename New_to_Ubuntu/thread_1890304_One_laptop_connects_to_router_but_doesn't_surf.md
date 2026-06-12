---
title: "One laptop connects to router but doesn't surf"
date: 2011-12-03
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-12-03
Hi Guys,

I have a strange situation.
I have three laptops  - one running Ubuntu 11.10, one running 11.04 and one running Crunchbang.

All three laptops can connect to our wireless router.

Only my 11.10 and Crunchbang machines as well as my iphone  can surf via the router however.
My wife's 11.04 machine acts like it has a DNS error.  Every attempt results in a page not found error.

There are no propitiatory drivers used on the system.

I think this is related to the most recent updates from Ubuntu.

(She didn't think to take notes on what exactly was installed during that update.) It seems to have developed this problem yesterday after the updates.

How can I see what was updated and if needed remove the updates?
How can I search for a better wifi driver, if that is the problem?

I'd really appreciate any help.
Does anyone have any ideas or has anyone had this happen as well?

---

### Post by Basher101 on 2011-12-03
if you have DNS resolution problems, try setting an IP address manually. This usually works best at first. Just check the IP addresses of one of your other machines and copy it, only changing the last two digits. Everything else should stay about the same. Give it a go and post your outcome


regards

---

### Post by roger_1960 on 2011-12-03
Hi

You can check the DNS settings by looking at "connection information" in the network manager dropdown.  Are they the same for your working and non working PCs.  If not perhaps you can correct the settings in "edit connections"

---

### Post by GrouchyGaijin on 2011-12-03
> **roger_1960 said:**
> Hi

You can check the DNS settings by looking at "connection information" in the network manager dropdown.  Are they the same for your working and non working PCs.  If not perhaps you can correct the settings in "edit connections"

Yes the settings are the same.
I may be doing something wrong, but when I manually set the address etc. on the problem machine I'd get a "failed to connect" error almost immanently when I'd try to go to any page.

I kept everything the same as listed on the working machines except I gave the problem machine the address of 192.168.0.109

The odd thing is that if I connect via Ethernet to our wall, not the router, then switch back to wi-fi - this computer will surf fine until I logout then back in.

---

### Post by roger_1960 on 2011-12-03
Hi

Are you sure that the ...109 address is within the range allowed by your router configuration - often its limited to .10 to .50 or .100  I would try setting it back to auto DHCP.

---

### Post by GrouchyGaijin on 2011-12-03
> **roger_1960 said:**
> Hi

Are you sure that the ...109 address is within the range allowed by your router configuration - often its limited to .10 to .50 or .100  I would try setting it back to auto DHCP.
I tried 105 too - the other laptops are 101, 103 and the iphone is 104

---

