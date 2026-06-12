---
title: "HOWTO - Warty and the NetGear RP614 DSL Router"
date: 2005-01-08
forum: Outdated Tutorials &amp; Tips
---

### Post by mark on 2005-01-08
Because I've become increasingly concerned about security (see my posts elsewhere about Firestarter), I broke down & bought the **NetGear RP614** DSL router/firewall.  NetGear's web site touted it as Linux compatible, I've had less-than-thrilling results with Linksys - it all looked good.

Let me say right now that my ISP asigns static IP addresses, which is fine - apparently until you start mixing in a router/firewall.  I knew nothing of this...

Got it home, connected everything, fired it all up (per the NetGear documentation) and...no Internet.  Discouraging.  Went through all the troubleshooting stuff, no help...my "naked" DSL modem connected fine, with the RP614 in-circuit I got send but no receive.

Right - called NetGear's tech support line...went through a 10-minute wait, finally connected to someone that asked what version of Windows I was using.  I explained that I used Linux & he immediately said, "Oh...would you hold on for a minute?"  After somewhat more than a minute he comes back & says that, "Linux support is a different group" & gave me another toll-free number.  Called that - and discovered it was for NetGear's "premium" (pay-per-call) support...and they were closed, being the weekend.

Finally, in desperation, I called my ISP (Speakeasy), on the off-chance they'd heard something about this.  When I talked to Brice, he didn't have specifics about NetGear, but suggested that most routers "want" DHCP as opposed to static IP.  I changed my configuration via (*Computer>System Configuration>Networking* ), rebooted and - *eureka!* - there it was!  I then proceeded to log in to the router, do my basic configuration and now, all is well with the world.

I find it sad, though, that the hardware vendor has reached the point of referring Linux questions to their "SWAT" team, when the answer was so simple...

---

### Post by Quest-Master on 2005-01-09
Interesting.

We burned a few hundred dollars on connecting the house with LinkSys routers a while ago (before I got into Linux). I wish I had gotten D-Link or NetGear instead. :(!!!

---

### Post by FLeiXiuS on 2005-01-09
In return with what you have just mentioned, the particular brand of router has no concern on whether or not linux is installed on the network.  Windows and Linux mediums both share the same IEEE standards with networking.  It's not going to be a hardware issuse, unless you have configured your router horribly.  If you have any more concerns please consult me, and I will direct you the correct information.

---

### Post by mark on 2005-01-10
[QUOTE=FLeiXiuS]In return with what you have just mentioned, the particular brand of router has no concern on whether or not linux is installed on the network.  Windows and Linux mediums both share the same IEEE standards with networking.  It's not going to be a hardware issuse, unless you have configured your router horribly.  If you have any more concerns please consult me, and I will direct you the correct information.[/QUOTE]
I agree.  All things being equal, a router is a router is...well, you get the idea.

Really, the only problem I've had with LinkSys is that we've got several of their small hubs at work and after a random amount of time on-line, they just go "brain-dead"...can't find anything on the LAN.  Give 'em a power cycle and they're fine.  Maybe they were programmed by a Redmond refugee<g>.

---

### Post by netdroid9 on 2005-10-05
I'm pretty sure there's a setting to enter a static IP which should resolve this problem. Also, you might have needed to tell the router to use your computers MAC address instead of it's own.

---

