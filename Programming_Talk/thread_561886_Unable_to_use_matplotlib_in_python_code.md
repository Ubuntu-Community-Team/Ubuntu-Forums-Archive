---
title: "Unable to use matplotlib in python code"
date: 2007-09-28
forum: Programming Talk
---

### Post by anupamme on 2007-09-28
Hi,

In my python code, I am doing this:

from pylab import *

I have installed python-matplotlib, python-numpy, python-numarray, python-numeric (to be safe I installed everything). On the python prompt, when I do:

import advancedclassify

It gives this error:

Traceback (most recent call last):
  File "<stdin>", line 1, in ?
  File "advancedclassify.py", line 1, in ?
    from pylab import *
  File "/usr/lib/python2.4/site-packages/pylab.py", line 1, in ?
    from matplotlib.pylab import *
  File "/usr/lib/python2.4/site-packages/matplotlib/pylab.py", line 196, in ?
    import cm
  File "/usr/lib/python2.4/site-packages/matplotlib/cm.py", line 5, in ?
    import colors
  File "/usr/lib/python2.4/site-packages/matplotlib/colors.py", line 33, in ?
    from numerix import array, arange, take, put, Float, Int, where, \
  File "/usr/lib/python2.4/site-packages/matplotlib/numerix/__init__.py", line 75, in ?
    from _sp_imports import nx, infinity, rand, randn, isnan, all, any
  File "/usr/lib/python2.4/site-packages/matplotlib/numerix/_sp_imports.py", line 9, in ?
    from numpy import Int8, UInt8, \
ImportError: cannot import name Int8
--

On the other hand, when I use:

ipython --pylab

I can use matplotlib to plot.

Any help in resolving the above error, no matter how trivial it might seem to you will be appreciated.

Thanks
anupam

---

### Post by pmasiar on 2007-09-28
do you have numpy installed? Is the same error if you enter "from numpy import Int8, UInt8" in the python shell?

Also, don't do "from pylab import *" - it will pollute your namespace with Guido knows what. Always import only names you need. It will be also easier to debug later, when error will be reported associated with some name you will easily see where that name is coming from.

---

### Post by anupamme on 2007-09-29
>do you have numpy installed? Is the same error if you enter "from numpy import Int8, UInt8" in the python shell?

Yes, I get the same error when I enter this on python shell. So, do you have any solution to this?

>Also, don't do "from pylab import *" - it will pollute your namespace with Guido knows what. Always import only names you need. It will be also easier to debug later, when error will be reported associated with some name you will easily see where that name is coming from.

Thanks, I will take care of this but right now I am experimenting with the language and do not know which names I need.

---

### Post by pmasiar on 2007-09-29
> **anupamme said:**
> >do you have numpy installed? Is the same error if you enter "from numpy import Int8, UInt8" in the python shell?

Yes, I get the same error when I enter this on python shell.

For whatever reason, numpy is not installed properly. Check docs. Try installing it again. Ask on numpy mailing list.

---

