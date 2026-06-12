---
title: "[Python] Translating the PyPy Python interpreter?"
date: 2012-01-23
forum: Programming Talk
---

### Post by kramer65 on 2012-01-23
Hello,

I've been messing around with PyPy a bit and love the instant speed gains it facilitates. (up to three times as fast as with the normal python(2.7) with my code). I now read something [here](http://pypy.readthedocs.org/en/latest/getting-started-python.html) about "*Translating the PyPy Python interpreter*". Does this mean that it translates the PyPy interpreter to C code to effectively replace the normal python installation? And would this mean it is even faster than it is now?

It also says that "*When translated to C, it passes most of CPythons core language regression tests and comes with many of the extension modules included in the standard library including ctypes.*". Would this mean that I would in that case be able to use [scipy](http://scipy.org/) with it?

Or am I just talking nonsense here?  :?

---

### Post by MadCow108 on 2012-01-23
pypy is written in a restricted set of python which can in theory be translated into any other language. Existing translations are C and CLI.
C is the default you get when downloading the binary.
```
bin/pypy --info | grep translation.backend:
                                 translation.backend: c
```
This does unfortunatly not mean you can use all C-extensions like scipy yet.

If you would translate it to the CLI backend you cannot use C extensions (as you are then in managed code), but maybe you can use the CLI library instead.
Also you need to have a cli implementation installed (like mono)

I guess you can also skip the translation and run directly in rpython, but thats probably quite slow.

---

