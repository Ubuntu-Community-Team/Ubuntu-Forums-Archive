---
title: "Comptuer -&gt; Router -&gt; Ubuntu Server box -&gt; Modem -&gt; Internet?"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by jwright8 on 2012-05-23
I wanted to set up a Ubuntu Server 12.04 LTS box between my modem and wireless router for a firewall, preferably iptables or shorewall, a web server, a mail server, and a VPN.

Does anyone have a link handy to a tutorial for this type of setup for 12.04 LTS (or anything semi-recent)?  The only comprehensive, explanatory link I've been able to find is for 6.10 here:

[http://www.howtoforge.com/ubuntu6.10_firewall_gateway](http://www.howtoforge.com/ubuntu6.10_firewall_gateway)

Half of the stuff (like MailScanner) seems to be depreciated, unavailable, or generally will not work (ie apache2-ssl command used in this article).

Any help to point me in the right direction is much-appreciated.  Thank you!

---

### Post by mlentink on 2012-05-23
Any particular reason why you want to put the server in front of, rather than behind the router (which is usually equipped with a firewall as well)? For this there a quite a few howto's, just search on 'ubuntu' and 'perfect server' on Howtoforge.

---

### Post by sandyd on 2012-05-23
> **jwright8 said:**
> I wanted to set up a Ubuntu Server 12.04 LTS box between my modem and wireless router for a firewall, preferably iptables or shorewall, a web server, a mail server, and a VPN.

Does anyone have a link handy to a tutorial for this type of setup for 12.04 LTS (or anything semi-recent)?  The only comprehensive, explanatory link I've been able to find is for 6.10 here:

[http://www.howtoforge.com/ubuntu6.10_firewall_gateway](http://www.howtoforge.com/ubuntu6.10_firewall_gateway)

Half of the stuff (like MailScanner) seems to be depreciated, unavailable, or generally will not work (ie apache2-ssl command used in this article).

Any help to point me in the right direction is much-appreciated.  Thank you!
Use [zentyal]("http://www.zentyal.com/") instead. Just click and install the stuff that you need.

---

### Post by jwright8 on 2012-05-24
> **mlentink said:**
> Any particular reason why you want to put the  server in front of, rather than behind the router 

I intend on using the Ubuntu server for VPN capabilities to connect to a  computer on the router from outside... I just naturally assumed, for the sake of  simplicity, that that means it would need to be before the router. 

I have looked at the "perfect server" tutorials, but none really explain using two Ethernet cards to route traffic through the box.  A lot of them also use nginx; I am very familiar with Apache, so I'm hesitant to deviate from that, as from what I've read the only main differences/improvements between the two is that nginx uses less RAM.  I'd also imagine you'd need to use somethingl ike IPTables to forward the designated traffic.

If what I want to accomplish can be done behind the router, then I'm all for it; I just don't see how it could be.  

I want a computer from the outside world (and ONLY a computer whose IP I explicitly specify) to connect to the network (while said entire network behind the router will have outbound and inbound traffic limited to only where I specify) via a VPN, connect to one specific computer, and use miscellaneous things on that computer. I'll likely mount a network drive or something.    I naturally assumed that, in order to accomplish this, all traffic would have to be routed through the Linux box... the easiest way to accomplish that, or so I thought, being to put it in front of the router.  Although, I suppose it's worth noting that this router will have wireless disabled, and has VPN capabilities (from Cisco, though I'd rather not use it since I read some horror stories about the "VPN capability" on the router).

The mail/web server was more of an afterthought.

> **sandyd said:**
> Use [zentyal]("http://www.zentyal.com/") instead. Just click and install the stuff that you need.

I'd rather configure it on Ubuntu, if I can, for a number of reasons.

One, I'm not a big fan of companies that say "oh hey, use our Open Source product, but we'll restrict it just like non-Open Source software until you decide to pony up and pay some money for something you're not even guaranteed to completely understand."  

While, I guess, if push comes to shove I'll use it, I never really want to use anything where I don't understand exactly what's going on.

I already have a Ubuntu Linode that I have running a web server/mail server/SVN/game server (unrelated to the project/question at hand), so again if possible I'd like to stay on relatively familiar ground.

I will check it out, though; it's worth a shot.

Thanks for the help and advice so far guys.

---

### Post by sandyd on 2012-05-24
> **jwright8 said:**
> I intend on using the Ubuntu server for VPN capabilities to connect to a  computer on the router from outside... I just naturally assumed, for the sake of  simplicity, that that means it would need to be before the router. 

I have looked at the "perfect server" tutorials, but none really explain using two Ethernet cards to route traffic through the box.  A lot of them also use nginx; I am very familiar with Apache, so I'm hesitant to deviate from that, as from what I've read the only main differences/improvements between the two is that nginx uses less RAM.  I'd also imagine you'd need to use somethingl ike IPTables to forward the designated traffic.

If what I want to accomplish can be done behind the router, then I'm all for it; I just don't see how it could be.  

I want a computer from the outside world (and ONLY a computer whose IP I explicitly specify) to connect to the network (while said entire network behind the router will have outbound and inbound traffic limited to only where I specify) via a VPN, connect to one specific computer, and use miscellaneous things on that computer. I'll likely mount a network drive or something.    I naturally assumed that, in order to accomplish this, all traffic would have to be routed through the Linux box... the easiest way to accomplish that, or so I thought, being to put it in front of the router.  Although, I suppose it's worth noting that this router will have wireless disabled, and has VPN capabilities (from Cisco, though I'd rather not use it since I read some horror stories about the "VPN capability" on the router).

The mail/web server was more of an afterthought.



I'd rather configure it on Ubuntu, if I can, for a number of reasons.

One, I'm not a big fan of companies that say "oh hey, use our Open Source product, but we'll restrict it just like non-Open Source software until you decide to pony up and pay some money for something you're not even guaranteed to completely understand."  

While, I guess, if push comes to shove I'll use it, I never really want to use anything where I don't understand exactly what's going on.

I already have a Ubuntu Linode that I have running a web server/mail server/SVN/game server (unrelated to the project/question at hand), so again if possible I'd like to stay on relatively familiar ground.

I will check it out, though; it's worth a shot.

Thanks for the help and advice so far guys.
Zentyal is based on ubuntu.

More like Zentyal = ubuntu + web interface + zentyal cloud.

Only difference is that theirs a web gui.

---

### Post by jwright8 on 2012-05-25
I just got done trying it and went back Ubuntu server. I guess it was alright for a click click click done type of thing, but I don't think it was what I was looking for.  

Some options, like Static IP, refused to let you configure it manually (/etc/network/interfaces), and ironically enough the web interface part of that (at least for Static IP, DHCP worked fine) it kept dropping connections and/or not reconnecting at all.  After a while, whenever I tried to SSH into the box it would literally lock up.  I guess it might also be worthwhile to mention that I had two different types of networks on hand to try (T1/Cable), for the sake of testing I did straight from modem to box, and then modem to router to box.

Secondly, I wasn't a big fan of their firewall modules.  Thirdly, the "Save all changes" thing was annoying, to say the least, particularly since if you modified one thing manually, and another thing via web interface, it would get me to Save all changes and then overwrite my manual change (no matter if I had visited that page on the web interface and changed anything on it or not).

Yes, before you ask, I tested literally all of the hardware.  I also replicated this in another system with sort of similar specs (~500 gb HDD, 3 gb ram, etc.), as well as switching pieces of hardware out. 

Everything I had set up, which ironically only consisted of about 3-4 things (IPTables, Denyhosts, Snort, etc.), were taken literally verbatim from my Ubuntu server that I use on a daily basis for lots of things.  All in all, I think I reformatted around 3 or 4 times to try it again and again with similarly disastrous results.  The last time I reformatted, I went straight to working on the static IP and had nothing but problems out of it again, so the system got reformatted again with 12.04 LTS Ubuntu server.

As an aside, GUIs (if you can do without them) pose security risks as a whole (X/KDE included).  

Does anyone have any tutorials handy newer than the 6.10 for Unbuntu server one I posted?  If not, I'll try some of those 'perfect server' tutorials and try to adapt it, but I don't hold much faith in that working out so well for me.

Thanks for the help so far everyone.

---

### Post by frotzed on 2012-05-25
I would advise against putting your main server and your firewall in the same physical hardware, gotta keep 'em separated. That way if the firewall gets hammered and starts dropping packets, your server is still inaccessible.

---

### Post by jwright8 on 2012-05-25
> **frotzed said:**
> I would advise against putting your main server and your firewall in the same physical hardware, gotta keep 'em separated. That way if the firewall gets hammered and starts dropping packets, your server is still inaccessible.

That makes sense; I had considered much the same thing, but it's good to hear it confirmed by someone that knows.

What about just running an Internet->Modem->VPN/Firewall->Router solution (with the VPN and firewall on the same physical hardware)? I would be perfectly happy with that, and would appreciate it if you could point me into the right direction for it.

Again, if the VPN thing is possible while placing the Linux box behind the router, I'm also open to it as well; I just don't see how it could be possible/workable.

It might also be worth re-mentioning that I'm primarily looking for a VPN solution, the firewall was just so I could block literally everyone incoming but specific IPs I allowed.

---

### Post by mlentink on 2012-05-25
Of course you can set up a vpn behind the router. Check the relevant pages in the ubuntu server guide on openvpn., or the openvpn tutorials. I run one, works like a breeze.

---

### Post by frotzed on 2012-05-25
> **mlentink said:**
> Of course you can set up a vpn behind the router. Check the relevant pages in the ubuntu server guide on openvpn., or the openvpn tutorials. I run one, works like a breeze.

The cool thing is there's more than one way to skin this cat.  I personally run a basic setup in my home: 

Internet > Modem > Router/Firewall -- Server & Computers

If I were to dedicate some kind of IDS like a Firewall on its own separate piece of hardware then I would do it like this:

Internet > Modem > Firewall > Server (set up for DNS and DHCP serving) > Computers

I don't mind letting my Server do DHCP and DNS while at the same time serving up files or what-have-you.  What I don't want is that server also being the firewall.

---

### Post by jwright8 on 2012-05-25
The only problem is that I'm kinda skeptical on router firewalls; are they really that dependable? 

I intend on locking almost everything down outgoing (and ONLY allowing that VPN port incoming), and my idea as using the Linux box to filter traffic (outgoing, say someone tries to go to facebook.com and it blocks it) I thought might be a good idea.  Sure I guess I could use a client-side software, or the routers built in functions, but I just feel like having more control over it would be a good thing.  I guess that's kind of the reason I was stuck on the idea of putting the server in front of the router (so everything has to go through it).

As for the setup of OpenVPN, I assume I just set it up as normal, then port forward on the router to the static IP of the machine?  This wouldn't open up any other holes in my network, would it?  I would assume it wouldn't.. but.. well... better safe than sorry.

I could then use IPTables to drop all IP's but the ones I explicitly allow, right?  I know how to block IPs, block ports, allow ports/IPs... but how would I go about blocking EVERY IP and only pick the ones I want to allow?

Like I said though, I'm more than open to suggestions; I'm obviously still learning, but I want to build the most secure network possible (locking everything down), then selectively opening one or two things to see how it all works.  Is there any better way to go about doing this than using a VPN (with IPTables) behind the router?  It's only really connecting one or two computers with Static IPs that I know the IPs of to connect to a Windows computer on the network and mapping a network drive (the network that the Ubuntu server will be on), while trying to block literally everything else (even web browsing).  The network needs to do only that one thing, really.

So like:

Computer 1 (remote) ----->  Modem/Router ----> Internet ----> ModemNetwork ----> RouterNetwork ---> UbuntuServerVPN | WindowsDestination      
( | denoting on the same "loop" I guess you would say)

Thanks for all the great advice so far!

---

### Post by frotzed on 2012-05-25
To be sure, the enterprise solution never involves a router/firewall combo unit.

---

### Post by jwright8 on 2012-05-25
So how would that work, though?  Assuming on the WindowsDestination, there were also systems on the LAN that needed to connect to it as well.  

For instance, let's say you had a modem, then a Linux firewall box, then a Linux box behind that to serve DNS/DHCP... would you have to have eth cards for each client that wanted to connect inside the DNS/DHCP server?  Or would you just run the eth1 of that server out into a switch?

---

### Post by frotzed on 2012-05-25
> **jwright8 said:**
> So how would that work, though?  Assuming on the WindowsDestination, there were also systems on the LAN that needed to connect to it as well.  

For instance, let's say you had a modem, then a Linux firewall box, then a Linux box behind that to serve DNS/DHCP... would you have to have eth cards for each client that wanted to connect inside the DNS/DHCP server?  Or would you just run the eth1 of that server out into a switch?

Switch and a wireless access point (if you wanted wifi).  It would be a managed switch, preferably.

---

