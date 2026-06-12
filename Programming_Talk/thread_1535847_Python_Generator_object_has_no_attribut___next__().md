---
title: "Python: Generator object has no attribut __next__()"
date: 2010-07-21
forum: Programming Talk
---

### Post by koala114 on 2010-07-21
I'm trying to figure out generator function, when I print __next__(), python says [PHP]AttributeError: 'generator' object has no attribute '__next__'[/PHP]

Has the __next__ method been removed from 2.6.5?

On my ubuntu box is Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56)

---

### Post by Compyx on 2010-07-21
The method is called 'next', no leading or trailing underscores.

---

### Post by StephenF on 2010-07-21
In python 3 you have __next__ and also a 'next' built-in function that calls the __next__ method.

```

a = (x for x in range(10))
# Python 2
a.next()
# Python 3
next(a)

```
This change is in keeping with the otherwise general uniformity of the language, or wart -= 1.

---

