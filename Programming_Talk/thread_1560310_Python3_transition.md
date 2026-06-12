---
title: "Python3 transition?"
date: 2010-08-24
forum: Programming Talk
---

### Post by worksofcraft on 2010-08-24
The all new Python 3 is on it's way so I ran the conversion program 2to3 on my scripts.

As it's not backward compatible now they won't run with Python2 giving errors like:
```

  File "./playbin2.py", line 22
    print("Error: {0} {1}".format(err, debug), file=sys.stderr)
                                                   ^
SyntaxError: invalid syntax

```

Alas they won't work with Python3 either... giving errors like:
```

Traceback (most recent call last):
  File "playbin2.py", line 2, in <module>
    import gst # gstreamer
ImportError: No module named gst

```

Luckily I kept all my backups, but it doesn't bode well for the future :confused:

---

### Post by Sockerdrickan on 2010-08-24
Well do you really have the gst module installed? (or maybe it's not compatible with 3.x)

---

### Post by GenBattle on 2010-08-24
yea you'll find most libraries such as gstreamer don't have python3 interfaces yet. Your code is probably perfectly python3 compatible, but you have to have compatible 3rd-party libraries as well (which is currently where python 3 is lagging behind).

---

### Post by bunburya on 2010-08-24
I don't know anything about the gst module but it could be one of the many modules that has yet to be ported to Python 3. Python has a large standard library so it takes time to port the whole thing. And if gst is not part of the standard library, then you'll need to go back to where you got it to see if it has been made compatible with v3.

Of course, you might just not have it installed.

---

### Post by juancarlospaco on 2010-08-24
*Not ALL battery are included for 3 yet...*
:)

---

