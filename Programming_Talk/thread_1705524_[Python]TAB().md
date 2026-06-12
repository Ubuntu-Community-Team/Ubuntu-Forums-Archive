---
title: "[Python]TAB()"
date: 2011-03-12
forum: Programming Talk
---

### Post by ki4jgt on 2011-03-12
In BASIC, I am allowed to use a feature called tab() which would allow me to align lists in the same columns in the terminal. Basically, I would

print x; tab(30); y

That would print x space over to the 30 character of that line and print y. anything like this for Python?

---

### Post by wmcbrine on 2011-03-12
I think the closest thing might be to use the .ljust() and .rjust() string methods. An example from my own code (Python 2.x syntax):

```
keynames = KEYS.keys()
keynames.sort()
for i, each in enumerate(keynames):
    print '   ', each.ljust(15), KEYS[each].ljust(15),
    if i & 1:
        print
```

This prints the contents of the KEYS dict in four columns. In your case:

```
print str(x).ljust(29), y
```

Or you could use the printf-style string formatting, or the new-style .format() string method.

---

