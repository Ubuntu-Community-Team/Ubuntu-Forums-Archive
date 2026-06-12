---
title: "help needed with PyQt and python 3... Help plz..."
date: 2009-11-21
forum: Programming Talk
---

### Post by python.noob on 2009-11-21
Hi friends,
               I'm using ubuntu 9.04.. I've not had any problem with the installation of pyqt as it is available from the ubuntu repositories with umpteen number of pcckages=D>=D>.. Thanks to ubuntu for making my job easier.. Anyhow i've to download tarball file for python 3.1 and installed it.. I found that PyQt4 supports python 3.1(Am i right?).. 

               I wanted to check the pyqt installation with a sample program..
```
import sys
from PyQt4 import QtGui
app=QtGui.QApplication(sys.argv)
widget=QtGui.QWidget()
widget.resize(250,150)
widget.setWindowTitle('Simple')
widget.show()

sys.exit(app.exec_())
```

                  when i issue the command 
```
$python simple.py 
```
it worked perfectly since it's executed with 2.6 installation.. 
             But when i tried to execute it with 
```
$python3 simple.py 
```
it showed the error like
```
ImportError: No module named PyQt4
```
           So i searched the sys.path for 2.6 and included 
```
/usr/lib/python2.6/dist-packages 
```
            in python3 sys.path...
          Now when i tried to run this with python3 the error is like..
```
ImportError: /usr/lib/python2.6/dist-packages/PyQt4/QtGui.so: undefined symbol: PyString_FromString
```
          I got the same error when i tried to execute another program too... So can u please tell me how to solve this problem?? Am i heading in the right direction... 

Thanks & Regards...

---

### Post by ikt on 2011-03-06
Just responding to this because it shows up as first result for me in google, 

the problem is that even though pyqt supports python 3, the modules for it haven't been properly installed, to say this was frustrating was an understatement.

After a lot of searching I found this:

[https://bugs.launchpad.net/ubuntu/+source/python-qt4/+bug/400826](https://bugs.launchpad.net/ubuntu/+source/python-qt4/+bug/400826)

"PyQt is not accessible from python3"

Which means you're going to have to build the pyqt4 modules manually.

A somewhat decent installation guide can be found here:

[http://ubuntuforums.org/showpost.php?p=10186123&postcount=6](http://ubuntuforums.org/showpost.php?p=10186123&postcount=6)

Also Qt Designer won't output python code by default or in the view code menu option, you will need to use pyuic to convert the code.

If I remember and they still haven't implemented python3 qt4 modules in 11.04 I'll probably have an install guide on my blog.

---

