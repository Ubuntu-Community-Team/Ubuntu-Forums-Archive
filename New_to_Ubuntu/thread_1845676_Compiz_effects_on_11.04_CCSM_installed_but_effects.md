---
title: "Compiz effects on 11.04: CCSM installed but effects not functioning"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by raequin on 2011-09-17
I have an old desktop computer, Athlon XP 2200+ and 2 Gb RAM, on which I recently installed 11.04, Natty Narwhal.  My problem is that I've come to really like a couple Compiz effects and I am unable to get any of them functioning.

I've changed the "Login Screen Settings" to use Ubuntu Classic as the default session.  I've installed CompizConfig Settings Manager, and ensured that Effects --> Animations is checked.  I've also got nvidia-current driver installed.

Oh, here's the solution.  I found it as I was writing this.  I'll go ahead and post this for posterity.

When I opened NVIDIA X Server Settings in System --> Administration, it told me that I was not using the NVIDIA x server and that I just needed to enter "nvidia-xconfig" as root and restart the x server.  So that's what I did and now the effects are working.

---

