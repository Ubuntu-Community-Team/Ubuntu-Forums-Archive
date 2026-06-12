---
title: "[SOLVED] transmission crawls"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by DarinB on 2008-08-23
Transmission crawls... in preferences says network automatically map port...and incoming TCP port xxxxxxxx closed...i have a linksys router...does this mean anything...can i tweak the speed or better to leave it alone...i could not add any other torrent client missing dependencies in synaptic???? why have anything in synaptic than can't be added???? confusing.

---

### Post by cozmicharlie on 2008-08-23
You need to forward your ports.  This site shows you how [http://portforward.com/routers.htm](http://portforward.com/routers.htm).  Go to your router and it will walk you through the process.  I have a Linksys router also and it is very easy.  Post back if you have any problems.

---

### Post by MrWES on 2008-08-23
connect to your router via [http://192.168.1.1](http://192.168.1.1) login and under port forwarding enable UPnP and you should be fine. I don't remember which tab it's under, as I'm running tomato firmware on my linksys router.

---

### Post by DarinB on 2008-08-24
i am upnpn enabled but it still clawls a will look into port forwarding.

---

### Post by drvid on 2008-10-15
I have had the problem of Transmission ports still being reported as **closed** even though I know UPnP is enabled and should be working on the router (it worked in Windows).

Last reboot I noticed some UFW firewall start-up, so I've since disabled it and now Transmission reports the automatic port forward as open! Finally!

Hopefully this increases my download speeds so that they are as fast as uTorrent in Windows was... We'll see.

In order to disable UFW open a Terminal and type

*sudo ufw disable*

---

