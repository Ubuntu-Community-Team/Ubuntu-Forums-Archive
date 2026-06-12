---
title: "4suite xml in Python: error importing"
date: 2007-05-22
forum: Programming Talk
---

### Post by anthro398 on 2007-05-22
I've used 4suite in earlier version of Ubuntu and, if I recall correctly, I've had this same problem.  I did apt-get install python-4suite-xml and 4suite installed fine, but I can't import anything from it.  I get this error:

```
>>> from Ft.Xml import Domlette
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 30, in apport_excepthook
    import apport.report, apport.fileutils
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 17, in <module>
    import xml.dom, xml.dom.minidom
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/__init__.py", line 220, in <module>
    from xml.dom import DOMImplementation
ImportError: cannot import name DOMImplementation

Original exception was:
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/Ft/Xml/__init__.py", line 160, in <module>
    from Ft.Xml.Lib.XmlString import SplitQName
  File "/usr/lib/python2.5/site-packages/Ft/Xml/Lib/__init__.py", line 12, in <module>
    from xml.dom import Node
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/__init__.py", line 220, in <module>
    from xml.dom import DOMImplementation
ImportError: cannot import name DOMImplementation

```

I think that in the past I've installed it manually from source, but I'd rather, of course, have it maintained by the repository.  Anyone else have this problem?  I wonder if the module is being deposited outside of my python path...  By the way, this Xpath, Xquery, XML library is pretty useful, quick, and simple.  I use it at work all the time.

---

### Post by anthro398 on 2007-05-22
Ok, so I was right.  The default install location when installing 4suite from the Ubuntu repository is /usr/share/pycentral/, which is not added to the python module search path.  This works: 

```
>>> import sys
>>> sys.path.append('/usr/share/pycentral/')
>>> from Ft.Xml import Domlette

```

But who wants to manually append to the path each time.  I see there is a config file at  /etc/python2.5/site.py
 that seems to deal with this, but it's confusing.

Does anyone know if this is where a new path should be added?

---

### Post by WW on 2007-05-22
The source of the error in the error message appears to be this:
```

    from xml.dom import DOMImplementation
ImportError: cannot import name DOMImplementation

```
Can you try that import statement by itself in an interactive python shell?  Here is what I get (in Dapper):
```

~$ python
Python 2.4.3 (#2, Oct  6 2006, 07:52:30)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from xml.dom import DOMImplementation
>>>

```

EDIT: Your second post showed up while I was editing, so you can probably ignore this!

---

