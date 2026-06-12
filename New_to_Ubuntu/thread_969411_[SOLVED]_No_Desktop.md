---
title: "[SOLVED] No Desktop"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by dstin1 on 2008-11-03
I installed 8.10 from the alt cd and now I get the login screen but no desktop just a blank tan screen anyone know what to do?

System specs
2.93GHz celeron
376 MB ram
intel 82845gl graphics card

thanks in advance

---

### Post by dstin1 on 2008-11-03
After doing a couple of searches I found several people are having this problem.  A solution was posted a few days ago and here it is

> **Drate said:**
> If you find you can get to the GDM but it won't finish logging you in (black screen, mouse moves), then goto a failsafe terminal session and do this:

sudo apt-get remove compiz compiz-core

That should fix ya (well, allow you to login to Gnome anyway).

There is a launchpad bug: 277373

---

