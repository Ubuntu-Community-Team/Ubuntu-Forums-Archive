---
title: "Setting up my linux VPS"
date: 2014-07-06
forum: New to Ubuntu
---

### Post by jared24 on 2014-07-06
[TABLE="class: table table-bordered table-striped solus_stats"]
[TR]
[TD]Status
[/TD]
[TD]                                     **online**[/TD]
[/TR]
[TR]
[TD]Type[/TD]
[TD]openvz[/TD]
[/TR]
[TR]
[TD]Template[/TD]
[TD]ubuntu-14.04-x86_64[/TD]
[/TR]
[TR]
[TD]Hostname[/TD]
[TD]             server1[/TD]
[/TR]
[TR]
[TD]Main IP Address[/TD]
[TD]198.12.79.3[/TD]
[/TR]
[TR]
[TD]IP Addresses[/TD]
[TD]198.12.79.3
[/TD]
[/TR]
[/TABLE]

That's my dashboard for my VPS. It was having problems with with connecting with the hostname when I had it as (server.domain.com)... after I switched to just having it as server1 it's been fine. The new problem is it can't get anything... here's a screenshot:[IMG]http://i.imgur.com/9QvAvm1.jpg[/IMG]

---

### Post by ubudog on 2014-07-07
Can you ping an external IP address, like Google (173.194.121.0)?

If so, but you can't ping "google.com", then it's probably a DNS issue.  What are the contents of your /etc/resolv.conf?

---

