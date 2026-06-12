---
title: "SSH no longer accepting remote requests"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by lazyart on 2008-09-23
For some reason SSH won't accept requests from outside my network anymore.  Used to run just great-- used NX Machine to get to my desktop from anywhere.   Won't work anymore and was able to trace it down SSH refusing my connection attempts.  From the LAN, everything is peachy.

Reinstalled openssh-server but that hasn't helped.  Anyone have any ideas on what would prevent external access?  Router is configured to forward port 22, just as it had been the whole time....

Any ideas?

---

### Post by superprash2003 on 2008-09-23
have you installed any firewall recently?? has the computer ip changed ? if so then you need to make appropriate changes to the router port forwarding settings..

---

### Post by lazyart on 2008-09-23
This machine has a static IP on the LAN.  No changes to the firewall.

---

