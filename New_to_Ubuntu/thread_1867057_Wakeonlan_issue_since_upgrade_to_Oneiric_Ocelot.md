---
title: "Wakeonlan issue since upgrade to Oneiric Ocelot"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by soriyath on 2011-10-22
I just thought I might share that.

I've installed Ubuntu 11.04 Server on my PC.  I mainly use wakeonlan, ssh. I would halt it from my macbook pro.

So I upgraded to 11.10 Oneiric Ocelot and I can't either wakeonlan nor power it down. Halt works but stops at "system halted", leaving me with the server powered up but halted.

After an hour looking on the forums I found that using "poweroff" instead of "halt" solved both my problems.

---

### Post by cavh on 2011-10-22
Anyone else reading this might also want to look at the ether-wake command (run in a terminal). I haven't used it myself but I heard about it just today on the Ubuntu-UK podcast.

[http://linux.die.net/man/8/ether-wake]("http://linux.die.net/man/8/ether-wake")

---

