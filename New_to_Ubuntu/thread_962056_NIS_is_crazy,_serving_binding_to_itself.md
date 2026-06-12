---
title: "NIS is crazy, serving binding to itself"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by TJCIB on 2008-10-28
My clients stopped being able to access the NIS server.  I cleared my iptables and disabled all firewalls.
Still, the clients could not even ping the server, but the server could ping the clients.

So I figured, it is an NIS configuration problem.
So I go back over the setup, making sure everything is okay.  I tried tweaking a few things, and stuff got screwier.

So i purged NIS and totally reconfigured.  Now, when NIS first starts (from install and all other restarts) it attempts to "Bind to YP Server"...even thought it IS the server.

I am trying not to be a noob at troubleshooting, but in the amount of time I've spent on this I could have backed up and reinstalled the OS on my 10 computers.

---

### Post by ChocoTuar on 2008-10-30
I'm having the same problem. Ubuntu hangs up during boot time once it hits the NIS services and keeps giving me the "* ...." while it tries to bind to YP server, never making any progress.

---

### Post by 480silverton on 2009-10-09
I know that this is slightly post but there are some wrong instructions in some HowTo areas

in /etc/defaults/nis
make sure that it is

NISSERVER=true
NISCLIENT=false

not (some instructions say master but master does not work)
NISSERVER=master
NISCLIENT=false

---

### Post by dchky on 2011-02-20
> **480silverton said:**
> I know that this is slightly post but there are some wrong instructions in some HowTo areas

in /etc/defaults/nis
make sure that it is

NISSERVER=true
NISCLIENT=false

not (some instructions say master but master does not work)
NISSERVER=master
NISCLIENT=false

Cheers mate, that did the trick :-)

Marked as solved for me.

---

