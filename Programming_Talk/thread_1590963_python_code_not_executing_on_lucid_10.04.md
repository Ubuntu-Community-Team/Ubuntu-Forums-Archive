---
title: "python code not executing on lucid 10.04"
date: 2010-10-08
forum: Programming Talk
---

### Post by Blackbug on 2010-10-08
i am running following code on ubuntu lucid 10.04
but when i execute it, gives following message

: No such file or directory

Code works when i run it using python interactive mode.
Also, it works on cygwin.

#! /usr/bin/env python

from pyExcelerator import *
import pprint

import xml.dom.minidom
from xml.dom.minidom import Node

doc = xml.dom.minidom.parse("books.xml")

mapping = {}
titleSet = []
authorNameSet = []
priceSet = []

i=0
for node in doc.getElementsByTagName("book"):
    isbn = node.getAttribute("isbn")
    L = node.getElementsByTagName("title")
    Author = node.getElementsByTagName("author")
    price = node.getElementsByTagName("price")

---

### Post by luvshines on 2010-10-08
Can you post the exact error, the way terminal gives it.

I just pasted your snippet as it is and tried to execute it, with correct indentation ofcourse for the 'for' block. Here is my output:
```
/tmp/python.py 
Traceback (most recent call last):
  File "/tmp/python.py", line 3, in <module>
    from pyExcelerator import *
ImportError: No module named pyExcelerator
```

---

### Post by spjackson on 2010-10-08
> **Blackbug said:**
> i am running following code on ubuntu lucid 10.04
but when i execute it, gives following message

: No such file or directory

Code works when i run it using python interactive mode.
Also, it works on cygwin.

#! /usr/bin/env python


I suspect that your script has DOS line endings (CR-LF instead of LF).

---

### Post by luvshines on 2010-10-08
> **spjackson said:**
> I suspect that your script has DOS line endings (CR-LF instead of LF).

And if that is the case, do:
```
sudo apt-get install tofrodos
fromdos <script-name>
```

Then try running it

---

