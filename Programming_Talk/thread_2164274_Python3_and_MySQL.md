---
title: "Python3 and MySQL"
date: 2013-07-31
forum: Programming Talk
---

### Post by lykwydchykyn on 2013-07-31
I've been a python programmer for some time now, and lately have the py3k fever.  I'm sold on Python 3, it's awesome, it has cool features, yada yada yada.  

So I'm trying to move some of my more important projects to Python 3.  Currently one of the big hurdles is the apparent (and rather stunning) lack of a solid mysql library.

Oracle offers the mysql.connector library for Python3 on Windows, but the .deb for Ubuntu (either from the Oracle website or the Ubuntu repos) apparently only installs for Python2.7.  When I try to import in 3, it can't find the library.

Apart from that, there are about half a dozen or more projects like moist, oursql, pymysql, etc that are either stalled or beta.

So far the only way I've been able to get a working mysql library in Python3 on Ubuntu is to set up a Py3 virtual environment and install with pip.  Unfortunately that's not a working solution because my software also requires PyQT and I have not been able to get PyQT or PySide running under a virtual environment.

So, tl;dr:  Which mysql library for Python3 on Ubuntu, and how do I install it?

---

### Post by lykwydchykyn on 2013-08-02
bump; nobody?

---

### Post by donsy on 2013-08-03
Don't quite know what you mean by "solid mysql library" but I've had good results with [PyMySQL3]("https://pypi.python.org/pypi/PyMySQL3/") so far.

---

### Post by lykwydchykyn on 2013-08-05
I guess what I mean is one that:

- Isn't beta/alpha
- Is being actively developed/maintained
- Has some degree of community consensus around it (or at least a high bus factor)

PyMySQL3 looks like a decent option, though according to the github page it's currently unmaintained.

---

