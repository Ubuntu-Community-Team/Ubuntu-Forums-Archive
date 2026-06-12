---
title: "ubuntu virtual domain name"
date: 2011-03-23
forum: Programming Talk
---

### Post by badperson on 2011-03-23
Hi,
I'm writing a web app I want to run on my home server. Right now, all of the internal links have [http://localhost:8080](http://localhost:8080), so when I try to run it on the server none of the links work.

I want to be able to just have [http://mysite.com](http://mysite.com). 

on the server, in my etc/hosts file I added 127.0.1.1 mysite.com
on my desktop, I added <ip for server> mysite.com

Is that all I need to do? (it didn't work...)
any idea how to set that up? 

Also, should I set up DNS on my server? 
thanks, 
bp

---

### Post by PaulM1985 on 2011-03-24
Does your main page work when you access it from your desktop?

You only need to set up some sort of DNS if your internal IP address changes for your home server.  Some routers allow you to fix your internal IP address for specific computers.

Paul

---

### Post by LoneWolfJack on 2011-03-24
DNS is a possibility, but if you just need a quick&dirty solution for development, have a look at this:

[http://www.thelampblog.com/2010/04/20/local-domain-names/]("http://www.thelampblog.com/2010/04/20/local-domain-names/")

---

### Post by slavik on 2011-03-25
don't use absolute paths in your anchors, use relative paths (ones that start with /).

sample of how you set up your links would be more than telling of what you are doing wrong.

---

### Post by badperson on 2011-03-25
the relative paths did the trick...would still like to use the domain name thing, though. will have to mess with it more.
bp

---

