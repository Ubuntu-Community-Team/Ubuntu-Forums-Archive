---
title: "Get cursor position in Python"
date: 2008-03-28
forum: Programming Talk
---

### Post by xelapond on 2008-03-28
Hello, 

Is there a way or command in Python to return the X11 cursor position?  I could not find anything on the Python mailing lists.

Thanks, 

Alex

---

### Post by LaRoza on 2008-03-28
PyGame has functions for that.

---

### Post by pmasiar on 2008-03-28
Python by itself does not have that - graphic library of your choice which communicates with X has.

---

### Post by days_of_ruin on 2008-03-28
> **LaRoza said:**
> PyGame has functions for that.
Darn, beat me to it!

:lolflag:

---

### Post by xelapond on 2008-04-01
> Python by itself does not have that - graphic library of your choice which communicates with X has.

That's convenient, I am using PyQT.  I looked up the documentation for it and found the QCursor class.  I tried this out in the python interpretor(I always do this before putting it into my main code), but every time I run it it segfaults.  Here is the code with outputs:

[PHP]alex@Andromeda:~$ python
Python 2.5.1 (r251:54863, Mar  7 2008, 04:10:12)
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from PyQt4 import QtGui, QtCore
>>> y = QtCore.QPoint
>>> x = QtGui.QCursor()
>>> y = x.pos()
Segmentation fault (core dumped)
alex@Andromeda:~$[/PHP]

Here is the documentation I used: [http://www.riverbankcomputing.com/Docs/PyQt4/html/qcursor.html](http://www.riverbankcomputing.com/Docs/PyQt4/html/qcursor.html)

Any ideas why its segfaulting? 

Thanks, 

Alex

---

### Post by tseliot on 2008-04-02
> **xelapond said:**
> That's convenient, I am using PyQT.  I looked up the documentation for it and found the QCursor class.  I tried this out in the python interpretor(I always do this before putting it into my main code), but every time I run it it segfaults.  Here is the code with outputs:

[PHP]alex@Andromeda:~$ python
Python 2.5.1 (r251:54863, Mar  7 2008, 04:10:12)
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from PyQt4 import QtGui, QtCore
>>> y = QtCore.QPoint
>>> x = QtGui.QCursor()
>>> y = x.pos()
Segmentation fault (core dumped)
alex@Andromeda:~$[/PHP]

Here is the documentation I used: [http://www.riverbankcomputing.com/Docs/PyQt4/html/qcursor.html](http://www.riverbankcomputing.com/Docs/PyQt4/html/qcursor.html)

Any ideas why its segfaulting? 

Thanks, 

Alex
Here's the description of QCursor:
> This class is mainly used to create mouse cursors that are **associated with particular widgets** and to get and set the position of the mouse cursor.

Here are the [full details]("http://www.riverbankcomputing.com/Docs/PyQt4/html/qcursor.html#details")

---

### Post by xelapond on 2008-04-02
Oh, so it was crashing because I didn't have  QApplication.  I wish some of the other bugs I had were that easy to fix:)  That doesn't look like the class I need though.  I could only find two other cursor classes for Qt, QDesignerFormWindowCursorInterface and QTextCursor, neither of which look like what I want.  Am I better off using the pygame one?  That seems a little weird to have a pygame module imported into a mail program, but I guess I can just import the one method.

Thanks, 

Alex

---

