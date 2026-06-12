---
title: "Python and server sockets"
date: 2007-02-16
forum: Programming Talk
---

### Post by oedipuss on 2007-02-16
What would be the correct or most useful way of binding a server socket in python? 
When I bind with **(socket.gethostname(), port)** others can't connect to me, maybe because I'm behind a router, even though I've seen the above way suggested in some tutorials, but when I bind with **('',port)** it works fine.
I suspect though that the empty string wouldn't work in other machines; that tutorial pointed out that it's binding only to localhost that way..  What's the best way to do it, so it works in general? 

thanks =)

---

### Post by jonathan_c on 2007-02-17
If you are using DHCP I think what is happening with (socket.gethostname(),port) is that it is binding to localhost/127.0.0.1 b/c socket.gethostname will return localhost/127.0.0.1 and not the IP address you get with DHCP

('', port') binds on all available IP addresses which is why it works.

---

