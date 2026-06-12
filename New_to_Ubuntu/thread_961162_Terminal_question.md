---
title: "Terminal question"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by Abu_Dayya on 2008-10-28
I don't know if this question fits in this subforum, but I didn't know where else to put it in. My question is:

I use ubuntu on my work pc to telnet to our UNIX servers. I think there is something in our routers and network configurations that if a connection to a server is idle for like 10 minutes, the connection get dropped, and its realy annoying. On windows, when using PuTTY, there was an option in putty that said "send keep alive packets every 10 seconds", and that will fix the problem. Is there something similar in GNOME Terminal.

---

### Post by Xiong Chiamiov on 2008-10-28
You really shouldn't be using telnet, as the protocol is quite insecure; ssh is much better, but if the servers aren't under your control, then there's nothing you can do about that.

So I found [how to specify keep-alive packet sending in ssh]("http://ubuntu.wordpress.com/2006/02/03/keeping-ssh-sessions-alive/"), but there's not as much information on telnet.  The manpage for telnetd [suggests]("http://manpages.ubuntu.com/manpages/dapper/man8/ktelnetd.html") that keep-alive is the default (look under -n).

---

