---
title: "Access ones own shell through proxy"
date: 2009-11-25
forum: Programming Talk
---

### Post by niiize on 2009-11-25
title sums it up pretty well..

thnx in advance for tips

---

### Post by iponeverything on 2009-11-25
> **niiize said:**
> title sums it up pretty well..

Seriously? I don't think it is clear. I am guessing that you mean being able to ssh into your machine when behind a firewall or ipmasqurade.
> 
thnx in advance for tips

Assuming the above, you can setup a reverse tunnel with ssh or configure your firewall or router to forward port 22 to the internal machine.

---

### Post by niiize on 2009-11-25
yes. i have a script using sockets on my machine, which i want use to connect to irc with, but through a proxy to be able to do it from another IP. thats the thing.

-n

---

### Post by niiize on 2009-11-25
have tried to use online web clients with proxys without any luck. i seem to get logged in, but immediately kicked, and i dunno what for. some how i am recognized as a proxyuser or something.

---

