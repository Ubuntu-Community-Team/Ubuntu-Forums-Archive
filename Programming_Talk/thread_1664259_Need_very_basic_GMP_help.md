---
title: "Need very basic GMP help"
date: 2011-01-10
forum: Programming Talk
---

### Post by Noeperrin on 2011-01-10
First of i'm really new to linux and I'm using Geany in unbuntu 10.10.
I'd really appreciate a step by step guide on how to install the GMP library, I've looked through the documentation but the instructions aren't clear to me. I've downloaded and run a config file but when i try include it in my program it say it was unable to find it.
Im really trying hard to find instructions and its becoming frustrating. 
Thanks in advance.
Noe

---

### Post by MadCow108 on 2011-01-10
step 1: sudo apt-get install libgmp3-dev libgmp3c2

and your done

link flag is -lgmp

you seldom need to install software by hand on package based distros.
If you do the default install location is often set to /usr/local instead of /usr

---

### Post by Noeperrin on 2011-01-10
^^ Thanks so much

---

