---
title: "Mono 2 installation"
date: 2008-11-18
forum: Programming Talk
---

### Post by hoboy on 2008-11-18
Does anybody knows a way of installing mono2 [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page) ?

---

### Post by directhex on 2008-11-18
Don't. Wait until it's ready. pkg-mono is looking out for your best interests by not rushing unready packages.

But it IS being worked on
```
directhex@mortos:~$ dpkg -l mono-vbnc | grep ^ii
ii  mono-vbnc                                  2.0+dfsg-1~dhx1                                      Mono Visual Basic Compiler (VB.NET)
```

And even the future beyond it

```
jms@osc-franzibald:~$ dpkg -l mono-vbnc | grep ^ii
ii  mono-vbnc                                  2.2-1                                                      Mono Visual Basic Compiler (VB.NET)
```

---

