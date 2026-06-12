---
title: "Python 2.6 QT4"
date: 2012-07-28
forum: Programming Talk
---

### Post by SelbyRowleyCannon on 2012-07-28
I have some stone-age software the only runs on Python 2.6. When I try  to run it, I get: 

Traceback (most recent call last): 
  File "pesterchum.py", line 13, in <module> 
    from PyQt4 import QtGui, QtCore 
ImportError: No module named PyQt4 

I know that 2.6 is ancient, but I can't bring it up to date because the  program architecture is way beyond me. I have attached the source code,  none of you will probably have time to bring it up to date, but can you  please tell me either: 

What the correct module is and how to fix it, or 

Fix all references and send the file back to me. (I understand if you  don't have time for this) 

Thanks a lot, 
        -S :guitar:

---

### Post by lykwydchykyn on 2012-07-28
First, what version of Ubuntu are you running this on?

Second, why does it have to run on 2.6?

---

### Post by juancarlospaco on 2012-07-28
I think python-qt4 is not installed.

good luck...

---

### Post by SelbyRowleyCannon on 2012-07-29
> **lykwydchykyn said:**
> First, what version of Ubuntu are you running this on?

Second, why does it have to run on 2.6?

Ubuntu 12.04, and because the software is ancient, and it's way beyond my ability to bring it up to date. Also, python-qt4 is installed.

---

### Post by oldfred on 2012-07-29
I changed and now I forgot why. You can see I commented out the version similar to yours.

#from PyQt4 import QtCore, QtGui, QtSql, Qt
import sys
from decimal import *
from PyQt4.QtCore import *
from PyQt4.QtGui import *
from PyQt4.QtSql import *

---

### Post by spjackson on 2012-07-30
> **SelbyRowleyCannon said:**
> I know that 2.6 is ancient, but I can't bring it up to date because the  program architecture is way beyond me. I have attached the source code,  none of you will probably have time to bring it up to date, but can you  please tell me either: 

I cannot see any attached source code. Which version of python are you trying to use on 12.04? Is it 2.7.3 or python3?

---

