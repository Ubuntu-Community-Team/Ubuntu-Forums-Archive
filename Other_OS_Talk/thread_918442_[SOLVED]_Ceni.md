---
title: "[SOLVED] Ceni?"
date: 2008-09-12
forum: Other OS Talk
---

### Post by zmjjmz on 2008-09-12
So I've heard about ceni, and that it's a CLI wifi manager for sidux?
Is this right?
Because if so, it could be used in so many other distros...

---

### Post by Rotaj on 2008-09-13
Ceni is a CLI network settings manager for sidux, not just wifi. Since sidux primarily uses Debian repositories, have you checked to see if it is in Debian repositories?

This might give you more info regarding ceni.
[http://sidux.com/PNphpBB2-viewtopic-t-7194.html]("http://sidux.com/PNphpBB2-viewtopic-t-7194.html")

Ceni might also be available through any distro that uses smxi.

---

### Post by zmjjmz on 2008-09-13
Ok, inx-one gave me a link to it.
[http://mirror.aarnet.edu.au/pub/sidux/debian/pool/main/c/ceni](http://mirror.aarnet.edu.au/pub/sidux/debian/pool/main/c/ceni)
I'll mark this solved.

---

### Post by blackbelt_jones on 2008-11-11
Oh, this looks very very good!

Periodically, I've been problems with my DSL connection.  It just goes out, and the only thing I've been able to do is reboot reboot reboot and reboot until the connection comes back, and sometimes it takes all day.  And when I call my DSL provider, and I tell them I'm using Linux, they're no help at all.

The problem isn't in the connection.  It appears to have something to do with DHCP.   Eventually, after a period of years, I've discovered that I can get my connection by booting a Sidux disk, setting up the ethernet card to configure manually with CENI, and running pppoe-config until an access concenterator is detected (don't know what it is, but I know that I need one) and then I get my connection back manually... that is, by typing in my username and password.

And then I'm online!  Unfortunately I'm also using a Sidux.  No flash, no firefox, no iceweasel, nothing custom.   But I just installed CENI in Ubuntu, thanks to you guys, and now know that on my Ubuntu with KDE system (technically, it's not Kubuntu) the equivalent of pppoe-config is called pppoeconf.  So maybe I can get my connection back faster next time, with my harddrive installed Ubuntu System.

---

