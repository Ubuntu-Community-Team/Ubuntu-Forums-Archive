---
title: "Logitech Squeezeboxserver"
date: 2011-09-16
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by nick_stokie on 2011-09-16
Has anyone got a working Squeezeboxserver (SBS) running on Oneiric, please?

I was holding off the upgrade from Perl 5.10 to 5.12 for some time but have now upgraded (and a downgrade is non-trivial) and SBS fails to start - throwing up error messages about Perl / SQL modules.

There seem to be several threads floating around the Logitech forums with similar Perl upgrade issues. I think SBS got patched for 5.12.3 for one of the Fedora releases but Oneiric has 5.12.4 and this doesn't seem to be working.

I've tried the fixes mentioned or linked to in these threads but find myself chasing error after error after the fix didn't instantly work.
[http://forums.slimdevices.com/showthread.php?t=89467](http://forums.slimdevices.com/showthread.php?t=89467)
[http://forums.slimdevices.com/showthread.php?t=88832](http://forums.slimdevices.com/showthread.php?t=88832)

Very grateful if anyone could share their joys/woes. Cheers.

---

### Post by nick_stokie on 2011-10-12
Moving to LogitechMediaServer (new name) 7.7.0 fixed this issue for me, as it is built against the 5.14 version of Perl.

(7.7.0 is currently a release candidate from unstable/testing repository but due full release very soon)

---

