---
title: "Graceful testing with Python packages?"
date: 2011-05-24
forum: Programming Talk
---

### Post by DangerOnTheRanger on 2011-05-24
I bet many of you reading this have (or have had) a similar dilemma. :)

Here's the problem: I have a Python package whose directory structure looks like this:

```

/ -- Package root
    __init__.py
    tstmod1.py
    tstmod2.py

```Simple enough, right?
Here's what [FONT=Courier New]tstmod1.py [/FONT]contains:

```

class SillyClass(object):
   abc = 1

```And [FONT=Courier New]tstmod2.py[/FONT]:

```

import tstpkg.tstmod1

class SillyClass2(object):
   """
   A silly class.

      >>> s = SillyClass2()
      >>> print s.sc1.abc
      1
   """

   def __init__(self):
      self.sc1 = tstpkg.tstmod1.SillyClass()


if __name__ == '__main__':

   import doctest
   doctest.testmod()

```Again, pretty simple. Just a doctest.
However, an attempt to run [FONT=Courier New]tstmod2.py[/FONT] prints out:

```

Traceback (most recent call last):
  File "tstmod2.py", line 1, in <module>
    import tstpkg.tstmod1
ImportError: No module named tstpkg.tstmod1

```To fix this error, [FONT=Courier New]tstmod2[/FONT] must look instead like this:
```

if __name__ == '__main__':

   import sys
   sys.path.append('..')

import tstpkg.tstmod1

class SillyClass2(object):
   """
   A silly class.

      >>> s = SillyClass2()
      >>> print s.sc1.abc
      1
   """

   def __init__(self):
      self.sc1 = tstpkg.tstmod1.SillyClass()


if __name__ == '__main__':

   import doctest
   doctest.testmod()

```I *really* don't like how that looks. Does anyone have a better, more elegant solution (that does *not *use relative imports? Nice try. :P)?

---

### Post by simeon87 on 2011-05-24
Why do you have the package name in there? If you have two .py files in the same directory, you can just do:

file1.py:

```

class A:
    def __init__(self):
        self.my_attr = 3
```

file2.py

```

import file1

class B:
    def __init__(self):
        self.a = file1.A()
        print self.a.my_attr
        
B()
```

which prints 3 as expected when you run file2.py.

---

### Post by DangerOnTheRanger on 2011-05-24
Thanks for the quick reply!

Good question. I prefer more explicit names with importing, though if push comes to shove, I'll do what you suggested. 

Also, I don't know what the "normally used" Python convention is with this issue, so I'll try to find that out as well.

---

### Post by simeon87 on 2011-05-24
> **DangerOnTheRanger said:**
> Thanks for the quick reply!

Good question. I prefer more explicit names with importing, though if push comes to shove, I'll do what you suggested. 

Also, I don't know what the "normally used" Python convention is with this issue, so I'll try to find that out as well.

Yes, but explicit names don't work the same way as they do in other languages, such as Java. If you do 'import bla.module' then you're saying there's a module (module.py) in the directory bla, relative to where the current file is. But that means you don't need to use a directory name when the file you want is in the same directory.

---

### Post by DangerOnTheRanger on 2011-05-24
Again, good point.
Marking the thread as solved, and I'm switching my conventions.

Oh well, time to modify 150 different import statements... :)
Thanks for the help!

---

### Post by DangerOnTheRanger on 2011-05-31
Oops, this wasn't completely solved. Pylint is chastising me for using relative imports, which suggests there's a better way. Any ideas?

---

