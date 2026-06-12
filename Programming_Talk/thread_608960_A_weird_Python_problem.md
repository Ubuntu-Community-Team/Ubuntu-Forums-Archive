---
title: "A weird Python problem"
date: 2007-11-10
forum: Programming Talk
---

### Post by chainzz on 2007-11-10
I am learning Python. Today I wrote a real small Python program to learn how to import modules:

```
import time
thetime = time.strftime("%H:%M")
print "The current time is:", thetime
```

In Windows XP (with the Python interpreter from the Python website) this program runs perfectly. However, in Ubuntu 7.10 (64-bits), it does not.

When I run

```
python time.py
```

I get the following output from the terminal:

```
bas@computerbas:~/Desktop$ python time.py
Traceback (most recent call last):
  File "time.py", line 2, in <module>
    import time
  File "/home/bas/Desktop/time.py", line 3, in <module>
    tijd = time.strftime("%H:%M")
AttributeError: 'module' object has no attribute 'strftime'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/urllib.py", line 28, in <module>
    import time
  File "/home/bas/Desktop/time.py", line 3, in <module>
    tijd = time.strftime("%H:%M")
AttributeError: 'module' object has no attribute 'strftime'

Original exception was:
Traceback (most recent call last):
  File "time.py", line 2, in <module>
    import time
  File "/home/bas/Desktop/time.py", line 3, in <module>
    tijd = time.strftime("%H:%M")
AttributeError: 'module' object has no attribute 'strftime'
```

The weirdest thing is that it DOES work when I run the commands in the Python interpreter:

```

bas@computerbas:~$ python
Python 2.5.1 (r251:54863, Oct  5 2007, 13:50:07) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import time
>>> thetime = time.strftime("%H:%M")
>>> print "The current time is:", thetime
The current time is: 20:10

```

Any suggestions?

---

### Post by Kadrus on 2007-11-10
Try writing the code from terminal and not in text editor..
Open Terminal
Type Python
And type the code
Good luck :)

---

### Post by deuce868 on 2007-11-10
Try not naming your file the same module name as the module you're trying to import. 

Make your file test_time.py or something.

If that works make sure to read a bit on namespacing. 

HTH

---

### Post by chainzz on 2007-11-10
> **deuce868 said:**
> Try not naming your file the same module name as the module you're trying to import. 

Make your file test_time.py or something.

If that works make sure to read a bit on namespacing. 

HTH
You're the best. Naming it time.py was SO stupid of me! Thanks a lot for the help!

---

