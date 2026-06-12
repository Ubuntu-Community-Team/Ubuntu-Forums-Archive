---
title: "Stuck in TTY"
date: 2020-06-19
forum: New to Ubuntu
---

### Post by ph0t0gr4ph3r on 2020-06-19
Hey everyone! I'm pretty new to Ubuntu, besides having used it just a few times before.

Basically, I'm completely stuck in the tty after I restarted the machine. The only thing I did that MIGHT've caused this was that I purged Python3.8 because it was causing issues with a program.

Any help for this? It's version 20.04 LTS

Also I've already tried startx and ctrl + alt +7 with no luck unfortunately.

---

### Post by Impavidus on 2020-06-19
Purging Python 3.8 will cause all kinds of problems. It's a vital component of Ubuntu. I'm not sure your package manager will still work now, so fixing it by reinstalling Python 3.8 (and what other things were removed automatically as they depend on Python) may not be easy, but you can try.

Have you got good backups of all important documents? I ask because a fresh install may be the fast way out of your problem.

---

### Post by ph0t0gr4ph3r on 2020-06-19
Thanks! Luckily I only have a few programs installed so I think I'll just do a fresh install. Won't be making that mistake again lol

---

