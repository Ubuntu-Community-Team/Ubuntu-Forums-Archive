---
title: "A question regarding switching to Python 3000"
date: 2010-12-29
forum: Programming Talk
---

### Post by zhaotianwu on 2010-12-29
I've recently read about getting prepared for Python3000, and one piece of advice reads,"Stop using obsolete modules". What does "modules" refer to here? libraries? :confused:

---

### Post by OgreProgrammer on 2010-12-29
Yes. modules are the pythony name for libraries.

---

### Post by ziekfiguur on 2010-12-29
> **OgreProgrammer said:**
> Yes. modules are the pythony name for libraries.

Not exactly, a module is one python file or folder with an __init__.py file. A module can contain functions or classes that you can use, but it can also be a program itself. 
Libraries are usually made up of several modules.

For the switch to python 3000 they mean obsolete modules from the standard library, like popen2 (and lots of others).
See here for more info: [http://www.python.org/dev/peps/pep-3108/](http://www.python.org/dev/peps/pep-3108/)

@zhaotianwu I would advise you to thoroughly read the complete python tutorial. You can find it here [http://docs.python.org/tutorial/](http://docs.python.org/tutorial/) for python 2, and here [http://docs.python.org/py3k/tutorial/](http://docs.python.org/py3k/tutorial/) for python 3. (Read one of the completely and than look at a document with differences between python 2 and 3)

---

### Post by zhaotianwu on 2010-12-31
> **ziekfiguur said:**
> Not exactly, a module is one python file or folder with an __init__.py file. A module can contain functions or classes that you can use, but it can also be a program itself. 
Libraries are usually made up of several modules.

For the switch to python 3000 they mean obsolete modules from the standard library, like popen2 (and lots of others).
See here for more info: [http://www.python.org/dev/peps/pep-3108/](http://www.python.org/dev/peps/pep-3108/)

@zhaotianwu I would advise you to thoroughly read the complete python tutorial. You can find it here [http://docs.python.org/tutorial/](http://docs.python.org/tutorial/) for python 2, and here [http://docs.python.org/py3k/tutorial/](http://docs.python.org/py3k/tutorial/) for python 3. (Read one of the completely and than look at a document with differences between python 2 and 3)

Thanks ziekfiguur, are those non-standard library sometimes considered as obsolete? like some GUI builder libraries, pygame, for example?

---

### Post by ziekfiguur on 2011-01-01
> **zhaotianwu said:**
> Thanks ziekfiguur, are those non-standard library sometimes considered as obsolete? like some GUI builder libraries, pygame, for example?

Som third party libraries may have obsolete modules, you'll have to look into the documentation from those libraries to find out.
One thing thoug, a lot of third party libraries are not yet compatible with python 3. I believe pygame is, but numpy and PyGTK for instance not.

---

