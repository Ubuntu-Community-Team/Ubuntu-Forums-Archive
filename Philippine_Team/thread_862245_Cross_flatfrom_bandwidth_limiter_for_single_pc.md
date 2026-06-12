---
title: "Cross flatfrom bandwidth limiter for single pc"
date: 2008-07-17
forum: Philippine Team
---

### Post by dodimar on 2008-07-17
I have a small home network. 2 desktops (1 WinXP, 1 Linux/WinXP, 1 portable. I am using a Linksys wrt4gc v.2.0 router. I have no server.

My questions is, is there a bandwidth limiter (open source) that I can install on each PC so that when one pc is downloading something it won't eat up all the network/internet bandwidth?

Thanks...

---

### Post by iLoveRuby on 2008-07-17
In Windows, I love [NetLimiter]("http://www.netlimiter.com/").

In Linux, you can fairly easily do it with "squid".

First, find out if you already have squid:
```
squid -v
```

If you don't, get it:
```
sudo apt-get install squid
```

You'll need to use "delay pools" as described in the [documentation]("http://wiki.squid-cache.org/ProgrammingGuide/DelayPools#head-ea175e57fea26d31f8bf1dc889e96fca853c6a04").

---

