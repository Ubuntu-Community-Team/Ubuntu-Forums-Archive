---
title: "[SOLVED] “server not responding” msgs starting to appear in DreamWeaver"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2008-10-16
I have an Ubuntu Server on my small network that acts (among other things) as a Web page testing server. I have DreamWeaver set up to connect to our remote host for putting operations, and the testing server is our local Linux machine. It worked great, as testing a page was instantaneous over the LAN. 

Then something —I have no idea what—changed and now, when we test on server or try the “test” button on the site configuration menu, we get ten to fifteen seconds of “Server Not Responding / connecting to server,” then it connects fine. 

The server pings fine and I can connect via an OS (both Mac and PC) fine. It’s just that we went from instantaneous connection to an irritating delay. Any idea where I start diagnosing/fixing this?

Here is a bit of background on the machine. I’m sorry I’m not sure what’s relevant — if I forgot something, please let me know, and ignore anything that’s superfluous.

It recently upgraded to 2.6.24-21. The upgrade went fine, but I had to reinstall the [LAN drivers](http://sudan.ubuntuforums.com/showthread.php?t=881156). The Linbox is assigned an IP via the router’s (Linksys 310N) DHCP Reservation Table, based on the Linbox’s MAC address. I don’t believe I’ve set a static IP on the box (/etc/network/interfaces is generic and unmodified). I’m using ProFTPD and WebMin, but mostly with default settings. 

Any thoughts as to what it could be or how I could go about diagnosing the problem?

Thanks, 

Rhythm

---

### Post by Rhythmdvl on 2008-10-16
Problem solved:

For the use of anyone who someday finds this thread, here is how things worked out:

I went to the ProFTPD Server module of [WebMin](http://www.webmin.com/), then to Networking Options. I changed two entries:

Do reverse DNS lookups of client addresses? (From default to no)
Lookup remote Ident username? (from default to no)

I then restarted ProFTPD and voila, it worked like it did before!

[http://www.proftpd.org/docs/faq/faq_full.html#AEN341](http://www.proftpd.org/docs/faq/faq_full.html#AEN341)

---

