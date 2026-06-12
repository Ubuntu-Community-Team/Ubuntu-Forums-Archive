---
title: "Interacting with other programs"
date: 2008-03-26
forum: Programming Talk
---

### Post by DingoMD on 2008-03-26
I was wondering if there is any way to interact with other programs using C/C++.
Let's say I want to run a program, get some info from its output, and sent it some input when it asks something like "Input x:". Can this be done?

---

### Post by hums07 on 2008-03-26
> **DingoMD said:**
> I was wondering if there is any way to interact with other programs using C/C++.
Let's say I want to run a program, get some info from its output, and sent it some input when it asks something like "Input x:". Can this be done?

Interesting question. I am new to programming in linux and wish to know that as well. In Windows, there are techniques called DDE and ... (forgot another - been several years ago). I read about signals and slots inside a linux program. How about between programs?

EDIT: It's DDE and DCOM in Win$

EDIT: According to [http://wiki.tcl.tk/18445](http://wiki.tcl.tk/18445), you can only use pipe in linux... but I've read that Bibus and OpenOffice can communicate somehow. CMIIW.

---

### Post by DingoMD on 2008-03-26
Unfortunately piping is not enough for what i want to do. I need a way to make two programs "chat" with each other. :(
Thanks for the info anyway.

---

### Post by Glich on 2008-03-26
yes, I would like to know how as well. I guess you could do it over tcp....client and server style.

---

### Post by DingoMD on 2008-03-26
Look here:
[http://ioi2007.hsin.hr/tasks/day1/aliens.pdf](http://ioi2007.hsin.hr/tasks/day1/aliens.pdf)
More specifically at the "Interaction" and "Testing" sections. Unfortunately I don't have that "./connect" program, which seems to do exactly what I want.

---

### Post by Glich on 2008-03-26
take a look at [http://en.wikipedia.org/wiki/D-Bus](http://en.wikipedia.org/wiki/D-Bus)

I don't fully understand it but it looks promising.

---

### Post by ruy_lopez on 2008-03-26
Unix Domain Protocols is one of the standard ways for different programs to communicate. They actually use sockets similar to TCP/UDP, with an almost identical API, but are specifically designed for operating on the same host.

Other ways use FIFOs, Pipes and STREAMS (not to be confused with FILE *fp streams).

All these can be used from C (and, I imagine, C++).

---

### Post by Glich on 2008-03-26
thanks, I need to brush up on my C and C++ I think

---

### Post by nanotube on 2008-03-26
you could also use the actual network protocols to communicate - have the source program open a port on localhost, and the recipient program read data from the port.

---

### Post by DingoMD on 2008-03-26
Just found this:
[http://www.gidforums.com/t-3369.html](http://www.gidforums.com/t-3369.html)

Haven't tried yet, but seems to be what I want. Thanks everyone for your tips :)

---

### Post by hums07 on 2008-03-27
> **Glich said:**
> take a look at [http://en.wikipedia.org/wiki/D-Bus](http://en.wikipedia.org/wiki/D-Bus)

I don't fully understand it but it looks promising.

I believe this is it! Thank's for the link.

---

