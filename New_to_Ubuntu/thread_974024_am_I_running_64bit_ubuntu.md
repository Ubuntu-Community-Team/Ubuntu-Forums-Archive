---
title: "am I running 64bit ubuntu?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by afd on 2008-11-07
Hi.

Firstly, I'm obviously a noob.

I had a copy of Hardy installed via Wubi and I was generally happy with it apart from my WiFi not working... now I have upgraded to Ibex I can't remember what version of Hardy was installed (32 or 64bit).

I've found ways to check what version of ubuntu is running (8.04, 8.10 etc) but not how to check whether you have a 32bit or 64bit version of the OS.

Any takers?

---

### Post by Sockerdrickan on 2008-11-07
```
uname -m
```
i686     = 32 bit
x86_64 = 64bit

---

### Post by afd on 2008-11-07
cheers fella.

easy when you know how I guess :D

---

### Post by keplerspeed on 2008-11-07
Some simple terminal commands:

> uname --help

will give all the options avaliable for the uname command.
for example,

> uname -a

will print all system info.

---

