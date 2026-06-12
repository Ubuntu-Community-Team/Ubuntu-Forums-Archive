---
title: "Python3.6"
date: 2018-05-14
forum: Programming Talk
---

### Post by dannyk2 on 2018-05-14
I am running Ubuntu MATE 18.04 and i'm trying to learn Python3.6 and there is also Python2.7.15. Is it possible to make Python3 the default program that loads first in a terminal instead of Python2?

---

### Post by &amp;KyT$0P# on 2018-05-14
Just run [FONT=Courier New]python3[/FONT]

---

### Post by Carl H on 2018-05-21
Either run your script with python3 instead of python, or  add a Python 3 shebang at the top of your script and run it with ./yourscript.py

---

### Post by Skaperen on 2018-05-22
i have added symlinks so i can use shorter names in all users on my laptop:

```
lrwxrwxrwx 1 root root  16 May 21 23:14 /usr/local/bin/py -> ../../bin/python
lrwxrwxrwx 1 root root  17 May 21 23:14 /usr/local/bin/py2 -> ../../bin/python2
lrwxrwxrwx 1 root root  19 May 21 23:14 /usr/local/bin/py2.7 -> ../../bin/python2.7
lrwxrwxrwx 1 root root  17 May 21 23:14 /usr/local/bin/py3 -> ../../bin/python3
lrwxrwxrwx 1 root root  19 May 21 23:14 /usr/local/bin/py3.5 -> ../../bin/python3.5
```

i am considering making python3 be the default by changing this a bit.  maybe you might want to do that.  mine have today's date because i have a script that rebuilds everything and i ran it just a few minutes ago.

---

