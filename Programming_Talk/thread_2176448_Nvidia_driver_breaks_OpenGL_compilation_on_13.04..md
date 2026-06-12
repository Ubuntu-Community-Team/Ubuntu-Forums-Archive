---
title: "Nvidia driver breaks OpenGL compilation on 13.04."
date: 2013-09-24
forum: Programming Talk
---

### Post by georgelappies on 2013-09-24
Hi all

When I install the Nvidia proprietary driver in Ubuntu 13.04 I can longer compile any OpenGL code written in c.

I think the Nvidia drivers breaks or replaces the symlinks in the /usr/lib/ directory but unfortunately I do not know enough of how to fix it.

The error I get is that there is no rule to make libGL.so 

Just using the opensource driver works for compiling but it doesn't work for playing Diablo 3 and WoW ;)

I have reinstalled Ubuntu 3 times today and really do not feel like messing up again. Does anyboody know why this is happening and how to fix it please?

---

### Post by dannyboy79 on 2013-09-24
which nvidia driver are you referring to?

---

### Post by georgelappies on 2013-09-24
Hi dannyboy79, I installed the '313 Updates' one from the software center.

---

### Post by georgelappies on 2013-09-24
Using the standard 310 drivers from the repo seems to work.

---

