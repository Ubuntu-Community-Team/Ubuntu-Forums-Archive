---
title: "[SOLVED] Problem when using ping"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by sharks on 2008-08-06
this is the msg i get when pinging
> arvind@ubuntu:~$ ping -i [www.google.com](www.google.com)
ping: bad timing interval.

i get this always. i tried other websites.

---

### Post by kpkeerthi on 2008-08-06
When you use the -i switch you need specify the interval along with it, like so:

```
ping -i 2 www.google.com
```
* for 2 second interval delay

---

### Post by plucky on 2008-08-06
> **sharks said:**
> this is the msg i get when pinging

i get this always. i tried other websites.

Try ```
ping -i 5 www.google.com
```

You forgot to put in an interval.

Good Luck

---

### Post by Vishal Agarwal on 2008-08-06
dear sharks,

if your problem is solved pls mark your thread as solved.

---

