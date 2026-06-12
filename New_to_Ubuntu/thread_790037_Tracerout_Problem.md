---
title: "Tracerout Problem"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-11
hi guys,

i was trying to do a tracerout and it ask me to run sudo apt-get install traceroute
so i did 

when i try to tracerout again it gave me this message
tracert 202.137.171.113
The specified type of tracerouting is allowed for superuser only

how do i set my self as superuser?

---

### Post by ConMan318 on 2008-05-11
Stick a 'sudo' (without the quotes) in front of the command and enter your password when it asks.  So:

```

sudo tracert 202.137.171.113

```
In general, any time you need to do something as superuser in the command line you put 'sudo' in front; it is command meaning **su**peruser **do**.

---

### Post by appoloin on 2008-05-11
ahhh!!! gotcha! thanx

---

