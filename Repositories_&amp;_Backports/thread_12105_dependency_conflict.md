---
title: "dependency conflict?"
date: 2005-01-21
forum: Repositories &amp; Backports
---

### Post by ahab on 2005-01-21
I have a recent warty install and I was trying to install libgtk1.2-dev, but I was getting  some dependencies that I couldn't resolve.

If I try to install libgtk1.2dev, synaptic tries to install libx11-dev, but fails on:

libgtk1.2-dev:
 Depends: libx11-dev but it is not going to be installed
 Depends: libxext-dev but it is not going to be installed
 Depends: libxi-dev but it is not going to be installed

If I try to install any of those packages, or look at their dependencies, I get a problem. For example:  libx11-dev depends on libx11-6 (=4.3.0.dfsg.1-6ubuntu25), but version 4.3.0.dfsg.1-6ubuntu25.1 from warty-security wants to install instead.

Why is this a problem? Do security updates break dependencies like this, or do I have something configured wrong? It seems like some of the other security updates have similar naming conventions, so what else could be the problem here?

---

### Post by akurashy on 2005-01-22
i had the same problem so i fixed it like this

go to synaptic package manager -> settings -> reposatories -> put a check mark on all of them , and reload

then try again getting the package

(though that worked for me i dont guarantee it work for you)

---

### Post by ahab on 2005-01-22
Thanks. It's good to know that someone else had the same problem as me, so I don't have to sit and wonder if I screwed things up.

If I'm not mistaken though, I would be wary of enabling all those repositories as a solution unless you want to be running hoary (the unstable development branch). You may be able to keep a mixed system by pinning, but it's never worked well for me on debian.

---

