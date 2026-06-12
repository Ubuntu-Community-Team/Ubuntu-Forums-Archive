---
title: "Python: inherit Set objects"
date: 2010-04-19
forum: Programming Talk
---

### Post by CHW on 2010-04-19
Hello,

I want to create a class implementing cyclotomic cosets which inherits from Set ([http://docs.python.org/library/stdtypes.html#set-types-set-frozenset]("http://docs.python.org/library/stdtypes.html#set-types-set-frozenset")).

 I would like to inherit from Set, because I need methods from Set like intersection and so on, this would avoid me to reimplement the whole stuff.

But my method which I used in the past to inherit for example int or tuple did not work and I couldn't find any documentation helping me there...

Here is my code which fails:
[PHP]class K(set):
    "The class of cyclotomic cosets."
    def __new__(self, i, n):
        s = [i,]
        if i != 0:
            j = (2 * i) % n
            while j != i:
                s.append(j)
                j = (2 * j) % n
        return set.__new__(self, s)[/PHP]

If I would substitute the last line by "return set(s)" this would work, but then I create a set, not a K object.

Does someone has a suggestion how to solve this problem?

Regrads,
CHW

---

### Post by spillz on 2010-04-19
how about __init__ instead of __new__?

```

class K(set):
    "The class of cyclotomic cosets."
    def __init__(self, i, n):
        s = [i,]
        if i != 0:
            j = (2 * i) % n
            while j != i:
                s.append(j)
                j = (2 * j) % n
        set.__init__(self, s)

print K(2,3)

```

---

### Post by CHW on 2010-04-19
Thank you :)

Exactly what I wanted!

---

