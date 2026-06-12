---
title: "cherrypy / python / socket problems on Hoary"
date: 2005-07-18
forum: Programming Talk
---

### Post by llimllib on 2005-07-18
Yesterday, I was running the cherrypy ([http://www.cherrypy.org](http://www.cherrypy.org)) tutorials on my ext3 partition without any problems. It would run on my root drive, but not on my FAT drive. On the advice of someone on c.l.p ([link](http://groups-beta.google.com/group/comp.lang.python/browse_thread/thread/3cfc26ce98d81f3b/)), I changed the permissions to my DMZ drive, and it started working there.

After a reboot, however, it doesn't work anywhere. What happens is, cherrypy starts up its own server, listening for connections on 8080. This seems to happen correctly, and all the debugging info that was printed when it was working is printed when it's not. When I try to connect to it (firefox to [http://localhost:8080](http://localhost:8080), telnet localhost 8080), there is no response, but everything takes a *very* long time to time out.

It works fine on my windows partition, so I don't think it's a router problem. I tried 127.0.0.1 instead of localhost, and that doesn't help, so I don't think its a HOSTS problem. 

Furthermore, GNOME has stopped working since (I use XFCE, but I tried logging into GNOME to change some settings; gnome definitely worked when I changed the permissions to my DMZ), but I can't figure out how that could even be related, except that it's probably trying to contact 127.0.0.1 and getting the same exceedingly long timeout that I'm getting.

If you want any info from my system, just post a response; it's pretty standard Hoary with python 2.4 and a manually downloaded cherrypy 2.1.

Peace
Bill Mill

---

### Post by llimllib on 2005-07-19
Just thought I'd post that I fixed the problem... Somehow, I had disabled the initial setup of the loopback device. Thus, pinging 127.0.0.1 was not working. I had to go into /etc/network/interfaces and add the line "auto lo", then reboot. Once I did, everything was fine.

Peace
Bill Mill

---

