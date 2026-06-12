---
title: "whats useing my internet?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by nutpants on 2008-05-19
i have something downloading on my ubuntu and i dont know what it is

how can i tell what is accessing the internet?

nutz

---

### Post by vitorgatti on 2008-05-19
try these commands:

netstat -n |grep tcp
netstat -n |grep udp

or try without the "-n", to see the complete address

---

### Post by nutpants on 2008-05-19
> netstat -n |grep tcp
netstat -n |grep udp



that helped i could back track and see where i was connected and from that tell what was most likely the software connecting..

but there must be a way to tell what software is connected out.
some way to get a list of what software to connected to what ip address.

nutz

---

### Post by seshomaru samma on 2008-05-19
install etherape -that might help
```
sudo aptitude install etherape
```
its graphical

---

### Post by Monicker on 2008-05-19
> **nutpants said:**
> that helped i could back track and see where i was connected and from that tell what was most likely the software connecting..

but there must be a way to tell what software is connected out.
some way to get a list of what software to connected to what ip address.

nutz


```
sudo netstat -anltp|grep ESTABLISHED
```


That will give you a snapshot of all established connections and the process to which they belong.

Wireshark is another tool that could used to get more details.

---

