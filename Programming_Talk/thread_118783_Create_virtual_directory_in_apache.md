---
title: "Create virtual directory in apache?"
date: 2006-01-17
forum: Programming Talk
---

### Post by idn on 2006-01-17
Hi, I was wondering if someone knew how to create a virtual directory like you can in IIS?

I fouind this

[http://httpd.apache.org/docs/1.3/vhosts/name-based.html](http://httpd.apache.org/docs/1.3/vhosts/name-based.html)

But itts a bit confusing, I use DHCP so I dont know what my IP address would be each time.

Basically, I want so localhost/mysite to point to /home/idn/mysite




Thanks in advance!

Jon

---

### Post by Neeko on 2006-01-18
DHCP for a web server is generally not a good idea, as it will break if the dhcp server assigns a different ip to your web server.

Anyway, it sounds like what you need to do is just change the DocumentRoot part of the http config file, so that Apache serves pages from that directory. 

You don't need a virtual host for that. Name based Virtual hosts are used when you want to serve two or more different sites from one IP address.

---

