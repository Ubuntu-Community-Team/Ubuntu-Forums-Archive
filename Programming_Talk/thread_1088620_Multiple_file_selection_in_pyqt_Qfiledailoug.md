---
title: "Multiple file selection in pyqt Qfiledailoug"
date: 2009-03-06
forum: Programming Talk
---

### Post by KLIA on 2009-03-06
Hi Guy;

i am working on program that requires me to have multiple file selection to be loaded into my program once i browse through my home directory, here's my file dailoug code to lunch up my file browser... but it can only choose one file at the time..

files = QtGui.QFileDialog.getOpenFileName(self,  'Open file','/home/', ("Images (*.png *.tiff *.jpg)"))

Any idea how to implement multiple file selection?

down is a screen shot to clarify my inquiry 

Thanks

---

### Post by simeon87 on 2009-03-06
Google ([actual source](http://lists.trolltech.com/qt-interest/2002-05/thread01189-0.html)) tells me that there's a method getOpenFileName**s** for multiple file selection.

---

### Post by KLIA on 2009-03-06
Thank you man, it worked by changing getOpenFileName to getOpenFileNames but i still get the following error

waseem@home:~/Desktop/Project2/GUI$ python wrapphotodb.py 
Traceback (most recent call last):
  File "wrapphotodb.py", line 49, in _actionImport_Photos
    file=open(files)
TypeError: coercing to Unicode: need string or buffer, QStringList found

how to implement a buffer for the selected files

---

