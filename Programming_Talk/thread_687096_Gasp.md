---
title: "Gasp"
date: 2008-02-03
forum: Programming Talk
---

### Post by twooften on 2008-02-03
Ok, I have just started reading through the DiveIntoPython.org stuff.
I came across the first bit of graphics stuff, called "Gasp (Graphics API for Students of Python)" 
When I run the sample script...
>>> from gasp import *
>>> begin_graphics()
>>> Circle((200, 200), 60)

>>> Line((100, 400), (580, 200))

>>> Box((400, 350), 120, 100)

>>> end_graphics()


I get from the first line...
Traceback (most recent call last):
  File "/home/albert/programing/test.py", line 1, in <module>
    from gasp import *
ImportError: No module named gasp

I have done a bit of searching, found little... any ideas what is wrong...?

---

### Post by LaRoza on 2008-02-03
That means Gasp isn't installed (in this case).

I am not familiar with it, and I can't find it in the repositories. I will search...

<edit>
[http://pypi.python.org/pypi/gasp/0.4.5](http://pypi.python.org/pypi/gasp/0.4.5)
</edit>

---

