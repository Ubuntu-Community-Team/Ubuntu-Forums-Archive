---
title: "Python literal translation"
date: 2011-04-28
forum: Programming Talk
---

### Post by jdb91 on 2011-04-28
Hi all, trying to get python to write a windows batch script (bear with me) with a path in .  Easy enough, except it keeps using the \ (windows directory) as an exit sequence.  In shell, to get round this, you use ' ' instead of " "

Is there anyway of doing this in python?

e.g.

```
>>> print '\bin'
    in

```

 I know the easiest thing to do is just backslash the backslashes, but that becomes very long winded.

---

### Post by jdb91 on 2011-04-28
Ah! got it

```

>>> print r'\bin'
   \bin

```

Incase anyone else was wondering

---

### Post by StephenF on 2011-04-28
Take a look at os.path.join() and os.path.sep.

---

### Post by andrew1992 on 2011-04-28
os.path.join/sep is the way to go for multi-platform. If you want a quick n dirty Windows solution, use the double backslash. '\\'

---

