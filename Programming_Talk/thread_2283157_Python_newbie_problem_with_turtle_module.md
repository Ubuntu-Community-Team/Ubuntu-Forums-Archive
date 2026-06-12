---
title: "Python newbie problem with turtle module"
date: 2015-06-19
forum: Programming Talk
---

### Post by pozitronios on 2015-06-19
I am learning python3 from [here ]("http://www.openbookproject.net/thinkcs/python/english3e/hello_little_turtles.html")

On the specific exercise I get these errors:
```

Traceback (most recent call last):
  File "turtle.py", line 2, in <module>
    import turtle #allows us to use turtles
  File "/home/user/folder/lessons/turtle.py", line 3, in <module>
    wn = turtle.Screen() #creates a playground for turtles
AttributeError: 'module' object has no attribute 'Screen'

```

I have installed tkinter for python 3 but with no luck.

What am I doing wrong? 

Thank you

---

### Post by steeldriver on 2015-06-19
You have named your python script file with the same name as the module you are trying to import (i.e. turtle.py)

Rename it to something else such as 'myturtle.py' or 'exercise1.py' and try again

---

### Post by pozitronios on 2015-06-21
thanx steeldriver, I couldn't have thought that [s]however I still get the same error with a different filename [/s]

I hade to remove any files with "turtle" in the name and it worked

---

