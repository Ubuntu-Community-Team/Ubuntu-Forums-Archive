---
title: "The Case of the Mysterious Python Module Imports"
date: 2010-03-25
forum: Programming Talk
---

### Post by vik_2010 on 2010-03-25
I began learning python a while ago, and I recently wrote this simple module to copy files from one place to another.

[PHP]#!/usr/bin/env python

import shutil,sys

def copy(src,dest):
    shutil.copyfile(src,dest)
    
if __name__ == "__main__":
    copy(sys.argv[1],sys.argv[2])[/PHP]As you can see, writing it was quite unnecessary, since python already has its own copy function.

But check this out: 
Every time I write something else and check it out at the command prompt, if there's an error the following stack trace almost always shows up:  
> 
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/apport_python_hook.py", line 39, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.6/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.6/dist-packages/apport/report.py", line 17, in <module>
    import xml.dom, xml.dom.minidom
  File "/usr/lib/python2.6/xml/dom/minidom.py", line 21, in <module>
    from xml.dom.xmlbuilder import DOMImplementationLS, DocumentLS
  File "/usr/lib/python2.6/xml/dom/xmlbuilder.py", line 3, in <module>
    import copy
  File "/home/vikram/Desktop/Python/copy.py", line 10
Or something similar, with my little copy.py module at the very end.

Moreover, following the stack trace, I looked at xmlbuilder, and saw that at line three, it imports the copy module.
[PHP]
"""Implementation of the DOM Level 3 'LS-Load' feature."""

import copy
import xml.dom

from xml.dom.NodeFilter import NodeFilter
[/PHP]My questions are these:

1) How in the world is this copy.py module showing up in the stack trace, considering it's not on my default search path?

2) There's a copy.py module provided by the standard python 2.6 installation. How are the two copy.py's getting confused, considering that, even IF my folder on the desktop is part of the default search path, shouldn't the standard python dirs be checked first?

*** btw, the way i'm checking the default search path is by importing sys.path into the interpreter.***

Cheers, gentlemen,

-V

---

### Post by vik_2010 on 2010-03-25
no one!? any help would be greatly appreciated.

---

### Post by Tony Flury on 2010-03-25
The default search path for imports includes your current path, and that is searched first, as that allows you to create your own version of an other wise standard module - and test and develop your own mods.

try renaming your application to something like "mycopy.py" - and try it then

See [http://docs.python.org/tutorial/modules.html#the-module-search-path](http://docs.python.org/tutorial/modules.html#the-module-search-path)

---

### Post by nvteighen on 2010-03-25
Actually, Python's copy is meant for something else... It's about copying objects, not files.

---

