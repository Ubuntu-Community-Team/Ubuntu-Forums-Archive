---
title: "Is SSH a better alternative to setting up a VPN server?"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by HautingLu on 2008-10-15
I've been asked to look into setting up a secure point-to-point connection between two LANs in different countries.

The first LAN is made of client PC's. The goal is for these PC's to be able to connect (remote desktop) to an existing Windows Terminal Server and EoD server with Exceed on the second LAN.

LAN1: Client PC's w/ Windows XP. 
|
<VPN server>
|
|
<the tubes>
|
|
<VPN server>
|
LAN2: Terminal Server, EoD server, a PC, and a few Solaris machines.


On paper, putting a VPN server on each side makes the most sense. But briefly reading online sounds like VPN servers can be PITA's to setup.

I'm familiar with SSH already and in the past have setup my own ssh server that was being my router with DynDNS, port-forwarding, and keys.

But what I'm not clear about is how the two SSH servers would connect to each other so that it was a transparent connection for the clients and servers. 

I've done this in the past to remote desktop:
Client PC------SSH Server (with X11 tunnel)------->PC (to remote desktop)

This situation would obviously be different:
Client PC------SSH Server-------....---------SSH Server---------Terminal Server

Would the two SSH servers have to have a connection (with -X) to each other? Or would the user have to ssh from one SSH server to the next before being to remote desktop?


p.s. I should have posted this in the morning, the question even confuses me :mrgreen:

---

### Post by DSn0wMan on 2008-10-15
Typically you would setup a VPN between the two lans, and then run whatever protocol you want (ssh, rdp etc...) over the VPN.

---

### Post by Nxion on 2008-10-15
> **HautingLu said:**
> I've been asked to look into setting up a secure point-to-point connection between two LANs in different countries.

The first LAN is made of client PC's. The goal is for these PC's to be able to connect (remote desktop) to an existing Windows Terminal Server and EoD server with Exceed on the second LAN.

LAN1: Client PC's w/ Windows XP. 
|
<VPN server>
|
|
<the tubes>
|
|
<VPN server>
|
LAN2: Terminal Server, EoD server, a PC, and a few Solaris machines.


On paper, putting a VPN server on each side makes the most sense. But briefly reading online sounds like VPN servers can be PITA's to setup.

I'm familiar with SSH already and in the past have setup my own ssh server that was being my router with DynDNS, port-forwarding, and keys.

But what I'm not clear about is how the two SSH servers would connect to each other so that it was a transparent connection for the clients and servers. 

I've done this in the past to remote desktop:
Client PC------SSH Server (with X11 tunnel)------->PC (to remote desktop)

This situation would obviously be different:
Client PC------SSH Server-------....---------SSH Server---------Terminal Server

Would the two SSH servers have to have a connection (with -X) to each other? Or would the user have to ssh from one SSH server to the next before being to remote desktop?


p.s. I should have posted this in the morning, the question even confuses me :mrgreen:


IMO I believe that having a VPN server is the way to go in this case. We have a VPN server setup in the way you describe and it works like a champ. I have not heard of a way to set ssh in the way you desire it to be. I might be wrong on this.

---

### Post by The Cog on 2008-10-15
I don't think SSH is suitable for this application. You need a proper VPN. I would suggest using OpenVPN as this only uses a single protocol (UDP) that can work nicely through NAT routers.

You will need to enable packet forwarding on the two VPN servers, and configure your routers with routes to to the remote networks pointong to the VPN servers.

---

### Post by Zzl1xndd on 2008-10-15
I gotta agree with the others a VPN really is the way to go here.

---

### Post by HautingLu on 2008-10-15
Thanks!

Did run into OpenVPN after spending some time on Google.

---

### Post by kevdog on 2008-10-16
Use the openvpn firware contained on ddwrt and flash your router to the firmware -- that way the vpn is builtinto your router -- a much easier solution.

---

