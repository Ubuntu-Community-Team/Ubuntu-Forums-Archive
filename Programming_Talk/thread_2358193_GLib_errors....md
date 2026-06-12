---
title: "GLib errors..."
date: 2017-04-10
forum: Programming Talk
---

### Post by joreri on 2017-04-10
Hi,
I'm new to Ubuntu and having some difficulties with the cv. I'm also lost regarding paths, I think.
Your help would bee greatly appreciated!

I'm trying to get QT4 working in Python.

I copy what I see as the problem and are hope to get pointed in the right direction:
je@telecinesrv:~$ uname -a
Linux telecinesrv 4.8.0-46-generic #49~16.04.1-Ubuntu SMP Fri Mar 31 14:51:03 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
je@telecinesrv:~$ workon cv
(cv) je@telecinesrv:~$ python client/fcClient.py 
Traceback (most recent call last):
  File "client/fcClient.py", line 10, in <module>
    from fcDialog import fcDialog        #class defining our main window
  File "/home/je/client/fcDialog.py", line 1, in <module>
    from PyQt4.QtGui import *
ImportError: No module named PyQt4.QtGui


 Best regard and thanks,
Joreri

Line 10 in fcClient.py:
from PyQt4.QtGui import QApplication

---

### Post by dragonfly41 on 2017-04-10
It is a bit of a jungle ... Qt4 .. Qt5 .. PyQt
Here is another site to follow ... if you are sure you want to stay with Qt4
[https://www.riverbankcomputing.com/software/pyqt/download](https://www.riverbankcomputing.com/software/pyqt/download)

And you can pick up tips/tutorials from 
[https://forum.qt.io/](https://forum.qt.io/)

Also the programming subforum here in ubuntuforums might get more replies.

---

### Post by joreri on 2017-04-10
Thanks, I'll read your links.
Thought it just was a path or something....

Hi again,

Outside the cv I get the following result:
je@telecinesrv:~$ python client/fcClient.py 
Traceback (most recent call last):
  File "client/fcClient.py", line 8, in <module>
    import config #cross-module globals defined here
  File "/home/je/client/config.py", line 3, in <module>
    import cv2
ImportError: No module named cv2


So I figure I have a path problem. If I use sudo I get another result.

How can I add the env in the path and so on......

Thanks

---

### Post by deadflowr on 2017-04-10
*Thread moved to **Programming Talk***

---

### Post by joreri on 2017-04-12
Hello again,
I was able to solve this problem just by adding a ln from the site-package to the virtual env.

Now I have another problem:
(cv) je@telecinesrv:~$ python client/fcClient.py 
2017-04-12 16:38:41,167 - DEBUG - Win Shown
2017-04-12 16:38:41,176 - DEBUG - All Conns Established

(python:5415): GLib-GObject-WARNING **: cannot register existing type 'GdkDisplayManager'

(python:5415): GLib-CRITICAL **: g_once_init_leave: assertion 'result != 0' failed

(python:5415): GLib-GObject-CRITICAL **: g_object_new: assertion 'G_TYPE_IS_OBJECT (object_type)' failed

Any ideas?

BR,
L

---

### Post by joreri on 2017-04-12
Hello, continuing my quest for a solution...
I was able to test the pyqt4 with the code below. It works great and presented me with a window.

Does anyone know where the GLib... is configured or belongs to? I have matlibplot installed and I'm starting to suspect it...?

BR,
L 

import sys
from PyQt4 import QtGui


def main():
    
    app = QtGui.QApplication(sys.argv)

    w = QtGui.QWidget()
    w.resize(250, 150)
    w.move(300, 300)
    w.setWindowTitle('Simple')
    w.show()
    
    sys.exit(app.exec_())


if __name__ == '__main__':
    main()

---

### Post by thomasbeh on 2017-05-08
Hello jojeri,

I am new in this forum (hello to all members ;-) ). I stumbled upon your post because I am running exactly into the same problem when starting fcClient.py. Thus, I guess, you are trying to install the same Super8 or 16mm film scanner I want to use (great project I think!). 
I followed the instruction as described in [https://github.com/jphfilm/rpi-film-capture](https://github.com/jphfilm/rpi-film-capture) and installed/compiled cv-stuff. Since we were both running into the same problem: is there something missing in the description of the installation? 

Did you try to start the client  using test  parameter. i.e.: python fcClient.py test    ? (I found this parameter when looking into source code). On my side then I see the control window, but there is no client window that shall show the captured picture and, when logging into the raspberry, I do not see any command log showing that the pi is receiving commands when clicking into the control window.

Perhaps we should contact the author?

Best regards,
Thomas

---

