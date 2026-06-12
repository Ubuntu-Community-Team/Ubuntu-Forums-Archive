---
title: "Firewall Distro"
date: 2007-03-27
forum: Other OS Talk
---

### Post by mdjohnson on 2007-03-27
Hi all,

Does anyone know if there's anything similar to IPCop that would run on a Sun Ultra 5?  (It's sparc64 I think).

Cheers

Mike

---

### Post by mips on 2007-03-27
Firewall-1
Stonegate
Gauntlet

But those are commercial.

If I was you I would just slap OpenBSD onto it and use pf(packet filter). Firewall Builder provides an excellent gui to pf and others.

Google: SPARC firewall.
Google:OpenBSD firewall

You can even get books on OpenBSD security/firewalling (I actually came across some e-books the other day)

[http://openbsd.org/](http://openbsd.org/)  The documentation is excellent. Very hard to screw up if you follow the docs.
[http://www.google.com/search?q=firewall&domains=openbsd.org&sitesearch=openbsd.org&btnG=Search](http://www.google.com/search?q=firewall&domains=openbsd.org&sitesearch=openbsd.org&btnG=Search)
[http://insecure.org/](http://insecure.org/)
[http://www.chuug.org/talks/20040727/obsd-sun-fw.pdf](http://www.chuug.org/talks/20040727/obsd-sun-fw.pdf)  This guide can be made much easier if you use Firewall Builder to do the pf rules.

The more common m0n0wall, smoothwall etc distros are not available for sparc, mostly i386.

---

