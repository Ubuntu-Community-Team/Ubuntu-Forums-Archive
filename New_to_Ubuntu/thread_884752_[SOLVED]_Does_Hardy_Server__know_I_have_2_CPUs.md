---
title: "[SOLVED] Does Hardy Server  know I have 2 CPUs?"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by bvanpelt on 2008-08-09
I've just installed Hardy Server (i386, 32 bit) in a dual-processor (dual AMD 64 processors, not dual core) box. Without access to the many GUI tools, how can I tell if it knows I have two processors?
Thanks!

---

### Post by terry123b99 on 2008-08-09
I found out using a screenlets application, one that checks all my sensors. FYI Hardy fully supports Dual Core.

---

### Post by jerome1232 on 2008-08-09
This should get the info you need.

```
cat /proc/cpuinfo | less
```

---

### Post by hyper_ch on 2008-08-09
install htop, run it from the cli and if it displays two cpus then hardy knows about it

---

### Post by bvanpelt on 2008-08-09
> **jerome1232 said:**
> This should get the info you need.

```
cat /proc/cpuinfo | less
```
I have 2 cpus! Thanks!

> **hyper_ch said:**
> install htop, run it from the cli and if it displays two cpus then hardy knows about it
Ah - learned something new! I love htop! Many thanks!

---

