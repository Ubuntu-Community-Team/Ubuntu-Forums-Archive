---
title: "Basic Gufw firewall question"
date: 2012-05-20
forum: New to Ubuntu
---

### Post by Lynceus on 2012-05-20
Hello,
If you deny all incoming traffic, how can you see websites/listen to music through Internet.  Doesn't that require incoming traffic?

---

### Post by Lars Noodén on 2012-05-20
Generally it is not all incoming traffic that is blocked but only new connections that are not part of an outgoing connection nor related to another established connection.  

Incoming traffic that is the result of outgoing connections is usually allowed.  Technically those connections are known as [Established](http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html#USERLANDSTATES).

---

### Post by Lynceus on 2012-05-20
> **Lars Noodén said:**
> Generally it is not all incoming traffic that is blocked but only new connections that are not part of an outgoing connection nor related to another established connection.  

Incoming traffic that is the result of outgoing connections is usually allowed.  Technically those connections are known as [Established]("http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html#USERLANDSTATES").

Thanks for the quick reply.

It's good that i know that now, marking the thread as solved

Edit: thanks for the link 

):P

---

