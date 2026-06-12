---
title: "no internet on server"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by poordamnedfool on 2008-06-26
ok i have a samba server set up all of the internetworking works i can access all the files on the server from other computers on the network, i can also access the internet from all of the other computers on the network, but the server does not have access to the net.  any ideas?  thanks

---

### Post by jonabyte on 2008-06-27
```
ifconfig
```

from a terminal, check the ip settings like the gateway.

you don't mention if you use dhcp or static ip

---

