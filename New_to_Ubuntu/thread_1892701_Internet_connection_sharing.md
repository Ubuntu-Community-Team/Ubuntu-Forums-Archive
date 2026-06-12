---
title: "Internet connection sharing"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by Tomáš on 2011-12-08
Hi,

i have Ubuntu server with one ethernet card. I want to share internet connection via this server to rest of network. I have question. Can i do it with one ethernet card ? I wondering if is it possible like this :

SERVER ---- [ Switch ] ------ Router
______________/  |  \
___________PC1  PC2  PC3

---

### Post by wolfen69 on 2011-12-08
Since routers have more than 1 output, just go directly to the server from the router, then directly from the router to a switch. The server does not need to be connected to the switch.

---

