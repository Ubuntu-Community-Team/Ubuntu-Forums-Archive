---
title: "bandwidth limiter?"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by drsyntax on 2008-09-12
Hello,

i have an ADSL line, and a router with 4 ports, and 3 pcs at my home.
what i want to do is to connect all my pcs to my pc that has ubuntu to control bandwidth of each ip, i don't know how to that or how make my ubuntu box work as a traffic monitor ?
any ideas ?

Thanks, and any help is appreciated.
Tamer Mohsen.

---

### Post by EarloftheWest on 2008-09-12
What about the Bandwidth do you specifically want to control?

Many routers have Quality of Service capabilities built in. That might offer you the capabilities you need.

---

### Post by drsyntax on 2008-09-12
i want to figure out how to make my other 2 pcs connect to my ubuntu box and ubuntu box manage their traffic, may be it will act as a router ?
and i want to be able to limit bandwidth upon ips, and it will be great if i can get traffic graphs of each ip.

BTW, my router is TP-Link TD-W8910G
Thank you,

---

### Post by cariboo on 2008-09-12
Have a look at this howto:

[http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html](http://ubuntulinuxhowto.blogspot.com/2006/06/setup-your-computer-to-be-router.html)

The only change I would make, is instead of setting webmin up from a tar file, download the deb and just double click on it, the deb installer (gdebi) will take care of all the dependencies. This howto uses kubuntu, but setting it up in hardy would be the same.

jim

---

