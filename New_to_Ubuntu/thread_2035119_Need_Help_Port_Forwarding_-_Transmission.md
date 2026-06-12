---
title: "Need Help Port Forwarding - Transmission"
date: 2012-07-29
forum: New to Ubuntu
---

### Post by Derrick79 on 2012-07-29
I'm trying to open up port 51413 for transmission. I can download find but I'm not uploading much at all. I get confused when it ask me what ip address to forward to. I have a dsl modem that has a firewall on it then it goes to a wireless router that has a firewall on it and my computers are plugged into that. I have a bunch of different ip addresses to, my ipv4  my dsl modem has one and my wireless router has one, a broadcast address, default route and a primary dns. I allowed port 51413 in/out in GUFW .. Thanks for any help u can give me, I've been trying to figure this out for days thanks

---

### Post by miegiel on 2012-07-29
The truly paranoid can never have enough firewalls (no offense ;)), but I think you can do with at most 2 firewalls. 1 for your PC and 1 on either the router or the modem (which ever you prefer). 

In any case, you'll need to open port 51413 in both directions on every firewall you have and, if the router and/or modem use NAT, forward it to the IP address of the next device in the chain.

---

### Post by 3rdalbum on 2012-07-30
> **miegiel said:**
> The truly paranoid can never have enough firewalls (no offense ;)), but I think you can do with at most 2 firewalls. 1 for your PC and 1 on either the router or the modem (which ever you prefer). 

Two?

How about just one?

One firewall to protect the whole network, and you can safely forget about running firewalls on each individual PC on that network.

Anyway, if possible you should turn off all but one firewall, whether that be the modem's firewall or the router's firewall. If you can't turn either of them off, then have the modem forward every port to the router, and then have the router forward that one port to your Bittorrenting computer.

That is assuming that the router is running DHCP, not the modem. If the modem is running the DHCP server, then the modem should forward the port to the Bittorrenting computer.

Sound difficult? Well, there's an easier way, but I'm unsure exactly whether it works as advertised. Enable "UPnP" support on your modem or router (whichever runs the firewall) and then enable it in Transmission. This should handle the port forwarding for you, but about five years ago it didn't work correctly so I never tried it since then.

---

### Post by miegiel on 2012-07-30
> **3rdalbum said:**
> Two?

How about just one?

One firewall to protect the whole network, and you can safely forget about running firewalls on each individual PC on that network.

Anyway, if possible you should turn off all but one firewall, whether that be the modem's firewall or the router's firewall. If you can't turn either of them off, then have the modem forward every port to the router, and then have the router forward that one port to your Bittorrenting computer.

That is assuming that the router is running DHCP, not the modem. If the modem is running the DHCP server, then the modem should forward the port to the Bittorrenting computer.

Sound difficult? Well, there's an easier way, but I'm unsure exactly whether it works as advertised. Enable "UPnP" support on your modem or router (whichever runs the firewall) and then enable it in Transmission. This should handle the port forwarding for you, but about five years ago it didn't work correctly so I never tried it since then.

I said; *"at most 2 firewalls"*. That means 1 _or_ 2. And there are, I believe, valid reasons to have a firewall on your modem (or router) and on your PC.

As for [UPnP]("https://en.wikipedia.org/wiki/Universal_Plug_and_Play") (and [NAT-PMP]("https://en.wikipedia.org/wiki/NAT-PMP")), enabling that does make life easier for you and for the software running on machines on your network. But by enabling it, you do allow everything, malicious or otherwise, to configure your firewall for you.

---

