---
title: "Can I install Nvidia Driver whilst on Live CD?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by md152 on 2008-05-28
Hey um just trying to get Desktop effects to work but i think i need the driver. SO i downloaded the right one for my card and x32 Ubuntu.
I figured out how to install it but it said it needed to be run from the root file.
Is it saying that because im running off Live CD?
Is it possible to install it?

---

### Post by Golem XIV on 2008-05-28
The problem is that the installation requires a reboot, and since the Live session does not save any settings you would end up without the driver in any case.  You could try just logging off and back on but I not sure it would work.

Try installing it from System -> Administration -> Hardware drivers and instead of rebooting just log off and back on.

You could also look up a way of having a persistent LiveCD installation (i.e. one that saves settings).  There should be a couple of threads about it in this forum.

---

