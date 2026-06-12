---
title: "Sorting out python versions"
date: 2019-02-05
forum: New to Ubuntu
---

### Post by vysero on 2019-02-05
On this Ubuntu 12.04 system I have the ability to run: python, python2, python2.7, python3, python3.2, python 3.2mu, python3.3, python3.3m and python3mu. When I open a terminal, I would like the command:

python

to open up the python2.7 application and the command:

python3

to open up the python3.3 application. Can someone help me sort this out?

---

### Post by oldfred on 2019-02-05
Your 12.04 went EOF or end of life on April 28th, 2017.
You need to upgrade.

You also do not change default python that Ubuntu uses and new versions use python3 but will use 2.7 for a few apps still.
If you change defaults you may break Ubuntu.

Or best if not using default just to specify it in your python code.

---

### Post by vysero on 2019-02-05
Yes I know it is EOL, unfortunately the embedded application I want to build won't build on newer versions of Ubuntu. So if I run a script that was written in python3 the comp will automatically run it with python3.3 and not python3? The only problem I see with that is when installing new packages.

---

### Post by oldfred on 2019-02-05
What good is an application that only runs on a system no one should be using?

I normally make this first lines in my python, but I am no expert.

```
#!/usr/bin/python3
# -*- coding: utf-8 -*-
#
or this:
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
```

One is supposedly better than the other, but I forgot.
And I started using this when I had python2 as default. You should be able to specify any version you want.

---

### Post by vysero on 2019-02-05
Well the application runs on an embedded system so the user never knows but in order to build the system you have to be on the system in which it was created. Maybe I am just running into some odd behaviour is all. I tried installing pyqt4:

 ```
sudo apt-get install python-qt4
```

then I made a simple script:

```
import sys
from PyQt4.QtGui import *
app = QApplication(sys.argv)
button = QPushButton("Hello World", None)
button.show()
app.exec_()
```

and tried to run it:
```

robert@robert-Precision-Tower-5810:~/Desktop$ sudo python3 ./helloworld.py
[sudo] password for robert: 
Traceback (most recent call last):
  File "./helloworld.py", line 2, in <module>
    from PyQt4.QtGui import *
ImportError: No module named PyQt4.QtGui
```

I will try again appending 

```
!/usr/bin/python3
```

to the top of the script.


EDIT: So running sudo python2.7 ./helloworld.py works, I will look for a way to specify where to download pyqt4 or how to specify which version of python I would like pyqt4 to run on.

EDIT2) This worked: 
```
sudo apt-get install python3-pyqt4
```

---

### Post by oldfred on 2019-02-05
I am using 18.04 with python3 and pyqt5.

I have this in my notes, not sure if true or not now.

# Debian dropping qt4 in future Aug 2017

---

