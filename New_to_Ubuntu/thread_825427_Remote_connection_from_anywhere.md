---
title: "Remote connection from anywhere"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by MaximB on 2008-06-11
I want to connect inside my company to my home machine which runs Ubuntu.
I know that for Windows and Mac's there is "Log me in" service.
How can I do it with native to Linux program/website ?

---

### Post by PinkFloyd102489 on 2008-06-11
Well it depends on if you want command line (SSH) or to control it graphically (VNC).

---

### Post by MaximB on 2008-06-11
Well from a command link I can use ssh, no problem.
But I want a GUI program.
I want it to be very simple.

My home machine's IP is dynamic and that can cause a problem.
That's why I need an "ultimate" solution like logmein.
Both my home and work PC's running Linux. (Ubuntu and redhat).

---

### Post by Mongo5000 on 2008-06-11
As PinkFloyd102489 said, if you want something like windows RDC, then you can use either VNC or nomachine.

VNC works good, but its a tad on the slow side for me.

Nomachine works great, as fast as RDC, but I could never get Shadow sessions to work.  Shadow sessions is logging into the desktop you had a home instead of creating a new one.  That, plus I couldn't get the resolution to show right.

So Im sticking with VNC.  it just works and that makes me happy

---

### Post by howlingmadhowie on 2008-06-11
a lot of home routers allow you to register them be dyndns or similar (see [http://www.dyndns.com/services/dns/dyndns/]("http://www.dyndns.com/services/dns/dyndns/")). once you've done that, you can install an ssh server on your home system and activate port-forwarding for port 22 on the router (NAT--network address translation). 

because ubuntu (to the best of my knowledge) has no support for uPNP (which is a good thing), you will have to play around with port-forwarding on the router no matter if you use a vnc or whatever. 

however, if you do open up your home computer to the world, quite independent of the method you use, it would be a good idea to install a software like denyhosts to foil brute force attacks.

---

### Post by billgoldberg on 2008-06-11
> **howlingmadhowie said:**
> a lot of home routers allow you to register them be dyndns or similar (see [http://www.dyndns.com/services/dns/dyndns/]("http://www.dyndns.com/services/dns/dyndns/")). once you've done that, you can install an ssh server on your home system and activate port-forwarding for port 22 on the router (NAT--network address translation). 

because ubuntu (to the best of my knowledge) has no support for uPNP (which is a good thing), you will have to play around with port-forwarding on the router no matter if you use a vnc or whatever. 

however, if you do open up your home computer to the world, quite independent of the method you use, it would be a good idea to install a software like denyhosts to foil brute force attacks.

Ubuntu does have upnp support, I'm running a upnp server right now.

It goes without saying it's only available inside my home network.

---

