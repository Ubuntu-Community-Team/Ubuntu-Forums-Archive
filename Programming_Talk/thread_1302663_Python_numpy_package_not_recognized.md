---
title: "Python: numpy package not recognized"
date: 2009-10-27
forum: Programming Talk
---

### Post by chuse on 2009-10-27
Hi to all. I'm starting to use python. I installed version 2.6.1 from Ubuntu repository, and I also installed python-numpy, python-scipy and python-matplotlib, since I need to make some nice plots from my work. So, I try and I get

>>> from numpy import hist,randn
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named numpy

So, I tried reinstalling, etc, but I don't get it. Some help?

José

---

### Post by TheStatsMan on 2009-10-27
Try

```

from numpy.random import randn
from numpy import histogram

```

---

### Post by dimechen on 2009-11-15
Hi!
I have a similar problem to chuse. My system tells me that python-numpy is installed, but when I try to run 

python -c 'import numpy; numpy.test()'

all I get is an error message:

Traceback (most recent call last):
  File "<string>", line 1, in <module>
ImportError: No module named numpy

I also tried reinstalling matplotlib and numpy, but that didn't help. Can anyone tell me what to do?
Thanks!
- Dime

---

### Post by robert.faryabi on 2010-07-26
Hi there! I have the same problem.
I see the /usr/lib/python2.6/dis-packages/numpy, but when I import the package, I get

ImportError: No module named numpy

I tried to reinstall numpy and python.

Thanks

---

### Post by StephenF on 2010-07-26
You installed Python? Python is installed by default and the python-numpy package is for the default version.

Launch Python and note the version number. The 2.6 package directory runs with python 2.6.x.

---

### Post by robert.faryabi on 2010-07-26
I just did that
This is what I have in my /usr/bin
lrwxrwxrwx 1 root   root           9 2010-06-28 19:02 python -> python2.6
lrwxrwxrwx 1 root   root           9 2010-06-28 19:02 python2 -> python2.6
-rwxr-xr-x 1 root   root     2613296 2010-04-16 10:42 python2.6

so the links are pointing to python2.6.

Here is the python prompt

Python 2.6.5 (r265:79063, Jun 28 2010, 20:31:28) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

I even try to export the PYTHONPATH, or sys.path.append to point to the numpy direcotry.

I just realized that there are to directories on my system
/usr/lib/python2.6/dist-packages/numpy

but actually the __init__.py is linked to 
/usr/share/pyshared/numpy/

Do you have any idea

---

