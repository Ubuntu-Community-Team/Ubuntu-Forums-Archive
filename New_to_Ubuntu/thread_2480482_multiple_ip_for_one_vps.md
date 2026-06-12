---
title: "multiple ip for one vps"
date: 2022-10-31
forum: New to Ubuntu
---

### Post by aliborhani on 2022-10-31
I'm new to Linux and ubuntu
I have one vps with two public ip address (both are valid) for example IP1 and IP2, but when I ping them from another pc, only one of theme response to my ping, other one I got time out, can any one help me to fix this?
I setup http server on my vps,
http server response only to IP1, is there anyway to server response to both IP1 and IP2?
regards

---

### Post by TheFu on 2022-11-01
Networking in a VPS can be very complex.  Best to use their guides for setting up access that you want.  Since SNI has been working for about 15 yrs, most people don't need more than 1 public IP to host 1, 2, 10, 100, 20,000 websites on a single server. [https://cwiki.apache.org/confluence/display/httpd/namebasedsslvhostswithsni](https://cwiki.apache.org/confluence/display/httpd/namebasedsslvhostswithsni) explains.  All web servers and reverse web proxies should support that.

Networking is the same for all internet connected OSes, so the same stuff you need to setup on the OS you know is needed for Linux.  Best if you are very specific about IPs, netmasks, routes, and firewalls to get any help.  By default, Ubuntu doesn't enable a firewall, since there shouldn't be any network services running on a fresh install.  As you add network any network services, then you'd be expected to use tcp-wrappers and/or firewall rules to block as needed.

Details. Please.

---

