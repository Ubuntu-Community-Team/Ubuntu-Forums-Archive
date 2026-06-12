---
title: "A question from a novice about Wake on Lan and X server remotely."
date: 2018-06-12
forum: New to Ubuntu
---

### Post by omnitek on 2018-06-12
Hello,

I'm new to Linux and Ubuntu and wondering if the following is technically possible:

Using an old laptop I would like to SSH (over the net) into an Ubuntu server at home that will Wake On Lan a desktop PC running Ubuntu desktop. I will then SSH into the desktop PC and use it with X server remotely over the internet. I would then like to put the desktop PC to sleep again. 

Is this technically possible?

Thanks.

EDIT: A follow up question... is X11 server remotely OK for normal applications that don't depend on a lot of graphics etc?

---

### Post by TheFu on 2018-06-12
A few options.
Does your router or switch support  WoL?
Do you have a low-power computer, perhaps a raspberry pi, that you could use to send the WoL packet?

X/servers are on the local machine you sit at and the X/client is the remote system. This is backwards for almost all other client/server situations.

Using X11 remotely over the internet is a total security failure.  You can use **ssh -X** for x11forwarding through the ssh tunnel, which addresses the security, but terrible performance is normal. The remote program is the X/Client and the client talks to your local X/Server to display and for human interactions.  Try it. See how well it does or doesn't work. I've never been happy with remote X that wasn't on the same LAN.

For remote GUI applications, might want to check out **x2go**.  It adds a few layers, but actual network bandwidth used is drastically reduced for a much better user experience.  x2go is based on NX protocol which leverages ssh for authentication and tunnelling.  There are security considerations, but those are limited to inside the remote system itself, not the network layer or local, display, client. I've used x2go from 5 continents and it works from fine-to-great depending on the available bandwidth for productivity applications.  No video. No audio.

Wake-on-LAN.  It only works when another machine on the LAN sends the WoL signal packets.  That can happen from another computer or network device on the LAN.  It is a LAN broadcast, so it cannot happen over the internet or WAN.  In short, you need another running system to send the WoL packet.

BTW, I leave my 7 physical systems running 24/7/365.  Most use less then 35W, so it doesn't impact the power bill much at all. IMHO, spinning down storage is hard on the disks and reduces the lifetime.  Since I'm not a gamer, none of the systems use a power-hungry GPU, which would probably change my ideas about WoL completely.  For me, it just isn't worth it.  CPUs for the last 5+ yrs now how to drastically reduce power use when it isn't needed.

Anyway, hope this helps and welcome to the forums.

---

