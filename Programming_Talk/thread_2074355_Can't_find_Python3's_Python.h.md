---
title: "Can't find Python3's Python.h"
date: 2012-10-21
forum: Programming Talk
---

### Post by atavory on 2012-10-21
Hello,

  I'm trying to port a Python C extension to Python3 on Ubuntu 12.10. Building the extension using Python 2.73 (via "python setup.py build") works fine, but building using Python 3 (via "python3 setup.py build") fails due to not finding Python.h. Running "locate Python.h" confirms that it is present in "/usr/include/python2.7/", but absent from "/usr/include/python3.2mu", which is where distutils is looking for it. The Ubuntu Software Center indicates that Python 3.2.3 is fully installed. Where is the missing header? I'd appreciate advice.

  Thanks & Bye,

  Ami

---

### Post by MadCow108 on 2012-10-21
you need to install python3.2-dev or python3-dev for the default version

---

### Post by atavory on 2012-10-21
That was it. Many thanks!

---

