---
title: "[python] pcapy library needs root access"
date: 2009-05-17
forum: Programming Talk
---

### Post by pokerbirch on 2009-05-17
O.S: Ubuntu 8.10
Python Editor: Editra 0.4.85

Just a quick question. I'm working on a Python app that requires the pcapy library. The problem is that pcapy requires root access and i am not comfortable with running my whole app as root user. Is there any way i can give pcapy root permissions and make it work within my app WITHOUT having to launch Editra via sudo?

---

### Post by Frak on 2009-05-17
Use fakeroot. It'll make the program think it's root without giving it root.

---

### Post by pokerbirch on 2009-05-17
> **Frak said:**
> Use fakeroot. It'll make the program think it's root without giving it root.

Hmmmm, that's a solution, but it's not really the solution i was *hoping* for. I was wondering if i could run my app in "normal" mode without using any kind of root at all? In other words, can i somehow give pcapy the root access it needs and still import it into my app WITHOUT running the app as root?


EDIT:
Just tried fakeroot and it doesn't work anyway:
```
pcapy.PcapError: socket: Operation not permitted
```

---

