---
title: "[SOLVED] Squid doesn't mask clients ip"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by redmorning on 2008-06-24
i have configured a proxy server (squid 2.6.STABLE14) on a ubuntu gutsy 7.10 machine with an ip 194.27.192.196. After reading a lot of forums i reconfigured squid.conf (i think no need to post squid.conf here yet).at the end i set this proxy server as default in my browser. it works fine,i can reach internet on my proxy server,and squid is caching as it has to.

here is my question : when i use my proxy server on my browser, i am still surfing with my own ip on internet (controled from whatismyip.com).correct me if i am wrong but shouldn't i see the proxy servers ip (194.27.192.196) when i surf ? as i know proxy server must mask my ip.

i hope i told my problem clearly,thanks

---

### Post by Oldsoldier2003 on 2008-06-24
> **piratejackus said:**
> i have configured a proxy server (squid 2.6.STABLE14) on a ubuntu gutsy 7.10 machine with an ip 194.27.192.196. After reading a lot of forums i reconfigured squid.conf (i think no need to post squid.conf here yet).at the end i set this proxy server as default in my browser. it works fine,i can reach internet on my proxy server,and squid is caching as it has to.

here is my question : when i use my proxy server on my browser, i am still surfing with my own ip on internet (controled from whatismyip.com).correct me if i am wrong but shouldn't i see the proxy servers ip (194.27.192.196) when i surf ? as i know proxy server must mask my ip.

i hope i told my problem clearly,thanks
Is the proxy server on your home network? If this is the case you are likely getting that effect because you are sharing the same ip as your proxy...

---

### Post by redmorning on 2008-06-24
proxy server is at university (this is a little project about university library) and i am at home (:,so that's not the problem.
thanks anyway.

---

### Post by redmorning on 2008-06-24
problem solved,it is because the site whatismyip.com gave me wrong information,when i test my internet speed in the same site i saw the proxy servers ip as my ip.
thanks.

---

