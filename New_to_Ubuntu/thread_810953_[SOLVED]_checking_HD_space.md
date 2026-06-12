---
title: "[SOLVED] checking HD space"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by x88a on 2008-05-28
i have about:-
1. 10 GB for root
2. 1GB for swap bytes
3. 29B for home

how do i check the free space for root and home?

tq

---

### Post by SunnyRabbiera on 2008-05-28
you can open op the system monitor, located under system>administration>system monitor and go to the file systems tab.

---

### Post by utUtu on 2008-05-28
> **x88a said:**
> i have about:-
1. 10 GB for root
2. 1GB for swap bytes
3. 29B for home

how do i check the free space for root and home?

tq

In a terminal, execute this code

df -h

:guitar:

---

### Post by x88a on 2008-05-28
thanks

---

### Post by wootah on 2008-05-28
My favorite one is the Disk Usage Analyzer (In the 'Accessories') menu. This gives you a graphical over view of what's happening and you can pick what directories (/file systems) to use :)

Good luck!

---

### Post by stchman on 2008-05-28
> **x88a said:**
> i have about:-
1. 10 GB for root
2. 1GB for swap bytes
3. 29B for home

how do i check the free space for root and home?

tq

For root use the following command:

```
df -k /
```

For home use this:

```
df -k /home
```

The -k is for kilobytes.

---

### Post by utUtu on 2008-05-28
> **x88a said:**
> thanks

You are welcome.  Glad to be of help.

---

