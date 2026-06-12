---
title: "range() difference in Python2 and Python3"
date: 2009-01-22
forum: Programming Talk
---

### Post by MockY on 2009-01-22
Could someone explain to me what the difference is in the range() function between Python2 and Python3?

Python2:
```

>>> range(10)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

```
Python3:
```

>>> range(10)
range(0, 10)

```

As far as I understand, Python2 creates a list while Python creates a tuple.
It would be kind if someone could enlighten me on this topic.

---

### Post by Paul Miller on 2009-01-22
Not quite.  In Python versions before 3, range() creates a list, as you say.  In Python 3, it creates a generator.  Effectively, what they did going from 2 -> 3 was to remove xrange() and make range() do the same thing xrange() used to do.

---

### Post by MockY on 2009-01-22
When used in for loops, the result is the same though. It's just different in the interactive session...as far as I can tell so far. I can't use an interactive session in the same way anymore...but I guess that's life.

---

### Post by snova on 2009-01-22
```
>>> list(range(10))
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```

It's a little more annoying to use at the interactive prompt, but most of the time, we just used xrange in the first place...

---

### Post by slavik on 2009-01-22
Python3 is not the only one:

```

slavik@slavik-desktop:~$ perl6 -e 'say (1..6).WHAT'
Range
slavik@slavik-desktop:~$ perl6 -e 'say list(1..6).WHAT'
List

```

---

