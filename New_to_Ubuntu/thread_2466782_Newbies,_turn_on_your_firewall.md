---
title: "Newbies, turn on your firewall"
date: 2021-09-05
forum: New to Ubuntu
---

### Post by psychohermit on 2021-09-05
Hi Folks,

I would recommend all newbies turn on their firewall.

ufw is installed with ubuntu,  The graphical front end for it is not.  You can install it with
```

sudo apt-get update && sudo apt-get install gufw

```
Launch the gufw from a terminal with sudo and select the 'Home' profile and enable the firewall. It will block all incoming network traffic and allow all outgoing.  So everything still works. You can add rules for any legitimate incoming traffic if needed. I turned it on yesterday and it logged 574 incoming packets.  Some automated ssh username / password guesser i imagine.
Better safe then sorry even if you're not running any internet enabled daemons.

I don't know how the runlevels work in ubuntu, but the firewall survived a restart so I'm happy.

Just my newbie $0.02

--glenn

---

### Post by mastablasta on 2021-09-06
> **psychohermit said:**
>  It will block all incoming network traffic and allow all outgoing.  So everything still works. 

this is the default setting on system. no doors are open by default. it is mostly needed if you have to open doors. if you use router it has its own firewall as well.

---

### Post by TheFu on 2021-09-06
> **mastablasta said:**
> this is the default setting on system. no doors are open by default. it is mostly needed if you have to open doors. if you use router it has its own firewall as well.

That hasn't been true for a few years with Ubuntu desktop releases.  When they started including avahi as a core part of the distro, allowing inbound connections for zero-conf became required for that to work - so services on the LAN can be found.

But for most people using Ubuntu, their systems will be behind a router with a firewall and all ports closed, so nobody will be able to directly ssh into the system.  Plus, ssh isn't installed by default, so people who do install ssh are responsible for adding whatever security their system needs.  In general, I install fail2ban when I install ssh (or openssh-server) and that prevents brute-force attacks with default configs.

If you are on a University or work LAN, then running a firewall is always necessary.  I've found university networks to be full of crackers seeing what they can see.  Same in hotels.

For people seeking a little finer control over their desktop linux firewall, there's a project that is relatively new which acts more like the Windows firewall. It provides per-application controls - well - that's the intent.  A friend has been using it for a year and loves it. I tried an RC4 for a few days about 3 weeks ago and it didn't work on my systems. I can't recall the name now and it isn't in any repos.  The source is on github and they provide a .deb package there.

Found the name in my history - **opensnitch**.  There's a daemon and a UI. I think most people would need both.  Run it in discovery mode for a week to see what is happening.

---

