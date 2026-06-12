---
title: "Halt hangs"
date: 2011-10-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by iditude on 2011-10-03
Hello everyone,

I'm trying to shutdown my machine properly for WOL to work.

I'm an old debien user and I'm used to just "sudo halt" which passes all the right parameters for WOL (netdown=no...)

Since moving to oneiric, I can't shutdown the machine using "sudo halt". It stops a lot of things and just hangs there

But the strange thing is that is does work when issuing any of the following:
- sudo /sbin/poweroff
- sudo shutdown -h now
- sudo /sbin/halt -d -f -p -h 

the file /etc/default/halt is set for HALT=poweroff

I'm really confused here. Anybody has a solution?

Thanks

---

