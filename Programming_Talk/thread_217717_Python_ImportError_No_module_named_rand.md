---
title: "Python: ImportError: No module named rand"
date: 2006-07-17
forum: Programming Talk
---

### Post by stoffe on 2006-07-17
Hello, I'm trying to run a python script off a website ([http://www.strout.net/python/shaney.py](http://www.strout.net/python/shaney.py)) and it fails with this error:
```
stoffe@cartman:~$ python shaney.py
Traceback (most recent call last):
  File "shaney.py", line 7, in ?
    import rand
ImportError: No module named rand

```
From what I understand from Google and other sources, this should be a standard module that is included, and I can't find any obvious candidates otherwise in apt. I am running Ubuntu 6.06 and as far as I know it shouldn't have broken in any unexpected ways. Does anybody have any clues, is it a deprecated lib or something and how can I fix this?

---

### Post by scxtt on 2006-07-17
there is a 'random' module, as in **import random**:

[http://docs.python.org/lib/module-random.html](http://docs.python.org/lib/module-random.html)```
:> python
Python 2.4.3 (#2, Apr 27 2006, 14:43:58)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import random
>>> random.randint(1,100)
93
>>> random.randint(1,100)
37
>>>
```

---

### Post by stoffe on 2006-07-17
Thanks, using that instead throughout the script seems to have fixed it. I suppose rand is the old deprecated name or something though I only found pages indicating that it was indeed a valid module. :)

---

### Post by scxtt on 2006-07-17
seems like "random" has been used since at least the 1.5 days ... maybe it was a typo or someone was coding w/ another language on their brain ...

---

