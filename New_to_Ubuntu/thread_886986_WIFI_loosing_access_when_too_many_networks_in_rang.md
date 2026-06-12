---
title: "WIFI loosing access when too many networks in range"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by hhare on 2008-08-11
I am not 100% that I know the cause but I suspect that I understand this and just need a way to stop it.

I have a dual boot machine, Vista (which I hate to use) and Ubuntu 8.

It uses a Broadcom chipset for WIFI.

If I am in a cafe etc it works GREAT with ubuntu.
y connected
If I am at home it works GREAT with ubuntu.

When I am at my g/f's I can not stay connected with ubuntu.  Windows (yuck) works fine.  It appears to stay connected to the wireless router, 
e the ability to communicate.  I can't even ping the router.

My suspicion is that it has something to do with there being 20 networks in range there and the places where I have no trouble have only one or two.

Is it that Ubuntu is trying to look for other netowrks?  I do have roam enabled.

Help please

---

### Post by dacorr on 2008-08-11
could be lots of things,

firstly,

whats the manufacturer of the routers that you are accessing?

secondly try this network manager, seeems to handle wifi quite well

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Dac

---

### Post by lisati on 2008-08-11
Also check which channel your router is using, just in case there's a conflict with a neighbouring network.

---

### Post by hhare on 2008-08-11
I will check that.  However, I suspect that this has nothing to do with it since if this was the problem then I would expect a problem with Windows (yuck) too!

---

### Post by dacorr on 2008-08-11
both OS ave an issue with DNS packets, to clarify

some routers are only DNS forwarders, his affects both OS except Linux trys to fix it, windows ignores the problem.

Plus there is not exactly a wide range of frequencies available they will interfer, most common channels appear to be 6 and 11 but it depends on the wireless specifics.

---

### Post by hhare on 2008-08-11
The router is a netgear wgr614, for what that is worth.

What is the issue with DNS packets?

And, how can a router merely be a DNS forwarder, it is allocating DHCP and doing NAT translation at a minimum

---

### Post by chrisod on 2008-08-11
Does Network Manager (or any other Ubuntu wifi manager) have a way to block out unwanted networks? If it is an issue of too many networks for some reason, maybe you can simply blacklist the ones you don't care about?

I don't see any easy way to do it through the GUI, but maybe somebody has a definitive answer.

---

### Post by hhare on 2008-08-11
Chrisod, that is the sort of thing I was hoping for, if this is indeed the problem and I really don't know that it is yet, of course

---

