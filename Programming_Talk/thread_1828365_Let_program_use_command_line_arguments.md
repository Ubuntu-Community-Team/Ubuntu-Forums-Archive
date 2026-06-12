---
title: "Let program use command line arguments"
date: 2011-08-18
forum: Programming Talk
---

### Post by 7cardcha on 2011-08-18
You know how when you use a command line command you do something like this (I am using the yes command as example)

yes hello

And it will print out hello to infinity. How do you make a program that can take command line arguments?

---

### Post by cgroza on 2011-08-18
It is language dependent. You will have to tell us what language you are trying to do this in.

---

### Post by 7cardcha on 2011-08-18
Python.

---

### Post by Bachstelze on 2011-08-18
Use sys.argv:

```
import sys
print sys.argv
```

---

### Post by Arndt on 2011-08-19
> **Bachstelze said:**
> Use sys.argv:

```
import sys
print sys.argv
```

One can add that the name 'argv' here comes from the old convention in the main function of C programs to let the array of arguments be called 'argv' (v for vector, I suppose).

---

### Post by MadCow108 on 2011-08-19
for more advanced command line handling use argparse (python > 2.7 but its also available as extra package for 2.6) or optparse (python < 2.7)
[http://docs.python.org/dev/library/argparse.html](http://docs.python.org/dev/library/argparse.html)

---

