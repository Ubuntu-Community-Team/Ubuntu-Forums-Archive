---
title: "Python 2.7 vs 3.2 - Is v2 still being developed?"
date: 2011-06-06
forum: Programming Talk
---

### Post by jhonan on 2011-06-06
I noticed that there was a stable release of 2.7 last November. Is the v2.x branch still under active development? Or is 2.x for stability for legacy code, and any new projects should be done in 3.x ?

---

### Post by Vaphell on 2011-06-06
problem is that many useful libraries didn't get their 3.x compatible ports yet, so it's not so easy to give definitive answer.

---

### Post by TwoEars on 2011-06-06
> **jhonan said:**
> I noticed that there was a stable release of 2.7 last November. Is the v2.x branch still under active development? Or is 2.x for stability for legacy code, and any new projects should be done in 3.x ?

Well, for questions of this sort, I'd suggest the Python mailing list. Anyway, regardless, I would suggest creating a program in python 2.x if you need libraries, and use 2to3 to support 3.x too.

There will be no more main releases to the 2.x branch, only support and backports.

---

### Post by cgroza on 2011-06-06
I will switch to python 3000 as soon as my beloved wxPython gets ported.
So for it is the only thing that is keeping me back.

---

### Post by llanitedave on 2011-06-07
> **cgroza said:**
> I will switch to python 3000 as soon as my beloved wxPython gets ported.
So for it is the only thing that is keeping me back.

That, and Django.  Those are both pretty big players in the Python app world.

---

### Post by jhonan on 2011-06-07
> **llanitedave said:**
> That, and Django.  Those are both pretty big players in the Python app world.
Ah! Django - Thanks for reminding me. It's one of the main libraries I'll be using, so looks like I'll be on 2.7 for a while longer.

---

### Post by simeon87 on 2011-06-07
I'm still on the 2.x branch too. Even if you can technically switch, you have to consider whether your user can do so too. They may not have the libraries installed and/or the latest libraries may not be in the repositories yet. It's going to be a gradual transition.

---

