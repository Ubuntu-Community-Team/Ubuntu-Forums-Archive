---
title: "Ant-like tool that also supports C++?"
date: 2007-01-23
forum: Programming Talk
---

### Post by Dislimit on 2007-01-23
Ant-like tool that also supports C++?
Is there any cross-platform build tools like Apache Ant which removes the dreaded format problem of make,  but support both C++ and Java?

---

### Post by lnostdal on 2007-01-23
> **Dislimit said:**
> Ant-like tool that also supports C++?
Is there any cross-platform build tools like Apache Ant which removes the dreaded format problem of make,  but support both C++ and Java?

[http://www.scons.org/](http://www.scons.org/) (sudo aptitude install scons)

I avoid `make' at all costs.

---

### Post by Relain on 2007-01-23
make?
qtmake?
rake? -> it's ruby but you can pretty much make it do what you want

come to think of it why not: ruby / perl / python scripts ?

---

### Post by lloyd mcclendon on 2007-01-23
i believe ant contrib has a cc task

ant is pretty flexible i'm sure it can do waht you want.  +1 for ant

---

### Post by rekahsoft on 2007-01-23
> **lnostdal said:**
> [http://www.scons.org/](http://www.scons.org/) (sudo aptitude install scons)

I avoid `make' at all costs.

why avoid make?

---

### Post by lloyd mcclendon on 2007-01-23
because makefile is so old and cryptic.  i'm terrified of it.  it has been said that nobody really understands make.  on the other hand you can find 8 million idiots like me who are a whiz with ant.

have you ever seen a makefile for a large project?  forget it.  i've written some reuseable ant builds for large projects and they've turned out pretty well.  easy to understand & easy to maintain.  

the only downside of ant is that sometimes xml & the core tasks don't do what you need, so you have to resort to someone else's custom task, or even worse write your own with jython.

also makefile is basically a shell script, so it's not portable.

---

