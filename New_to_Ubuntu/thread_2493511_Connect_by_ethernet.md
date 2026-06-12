---
title: "Connect by ethernet"
date: 2023-12-17
forum: New to Ubuntu
---

### Post by evrytimeonline on 2023-12-17
Hi guys, i have linux and windows pc's and wish to connect them directly one each others only by using Ethernet cable without router, can be?
i already change some ip config and much more but windows still can't found linux pc :(

best regards

---

### Post by MAFoElffen on 2023-12-17
I use an Ethernet Null Modem cable and them set the addresses as static on the same NetID range.

RE: [https://help.harmanpro.com/PublishingImages/null-modem-crossover-ethernet-pin-outs/Pic04.jpg](https://help.harmanpro.com/PublishingImages/null-modem-crossover-ethernet-pin-outs/Pic04.jpg)

I keep a 4" Ethernet Null Modem cable in my tool set, with an RJ-45 Female-Female Adapter, so that I can use it with a regular Ethernet cable when I am on onsite service calls.

---

### Post by ActionParsnip on 2023-12-18
You can connect a PC to a PC. You may need to manually set the IP address on each interface as there will be no DHCP.

---

### Post by MAFoElffen on 2023-12-18
> **ActionParsnip said:**
> You can connect a PC to a PC. You may need to manually set the IP address on each interface as there will be no DHCP.
That depends if the NIC's of both devices have Auto MDI-X, like a switch does, on whether it needs an Ethernet null modem null modem cable. The reason I refer to that as that instead of a roll-over cable... As coming from Cisco, what they refer to as a roll-over cable as pinned-out diffrently, and is for connecting switch and router console ports.

This article explains the why of that better (is a good read): [https://www.practicalnetworking.net/stand-alone/ethernet-wiring/](https://www.practicalnetworking.net/stand-alone/ethernet-wiring/)

RaspPi4's, for example, are fairly new, but do not. It's still not universal for all.

---

### Post by SeijiSensei on 2023-12-18
For more than two machines, you'll probably need a switch.

Manually assign each machine a unique IP address in a common subnet like 192.168.1.0/24. By default Ethernet and IP use broadcasting to identify themselves to the network. All the machines chatter away and watch for packets with their IP addresses designated as the target. If so, they accept and process those packets.

A router makes this much easier because it will have useful things like a DHCP server to provide address information to clients, and perhaps a DNS server that maps the assigned addresses to their hostnames. Then if the clients use the router for their nameserver, they can run commands like "ping bobbys_machine" since the router will have established the link between that name and its IP address.

---

