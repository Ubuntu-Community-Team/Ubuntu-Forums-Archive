---
title: "netwroking problem on client server program"
date: 2007-11-28
forum: Programming Talk
---

### Post by belikewater on 2007-11-28
Try to run client server application 
running the client gave the message:

[COLOR="Red"]ERROR connecting: Network is unreachable[/COLOR]

running the server gave the message:
[COLOR="Red"]ERROR on binding[/COLOR]

tried to change port number but it doesn't help
may be the problem is that i try to run it at local loop back 127.0.0.0?

1. how can i solve the problem?
2. how can i detect free tcp port numbers at linux?
both files are attached

---

### Post by adelgado on 2007-11-28
The loopback interface is at 127.0.0.1, not at 127.0.0.0. The 127.0.0.0 is the loopback address.

Try changing 127.0.0.0 to 127.0.0.1.

More info at [http://www.faqs.org/docs/linux_network/x-087-2-issues.ip-addresses.html](http://www.faqs.org/docs/linux_network/x-087-2-issues.ip-addresses.html) .

---

### Post by belikewater on 2007-11-28
just a minuet ago i find it and fixed it by myself:oops:

thanks it help me to be positive on this matter

---

