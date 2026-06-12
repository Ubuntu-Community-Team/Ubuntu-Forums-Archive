---
title: "Help with random"
date: 2008-08-21
forum: Programming Talk
---

### Post by swappo1 on 2008-08-21
Hello,

This morning I wrote the following program in python and it worked when I tried it.
[HTML]#! /usr/bin/env python
# hilow.py

import random

number = random.randint(1, 100)
guess = 0


while guess != number:
    guess = input("Guess a number between 1 and 100: ")
    if guess < number:
	print "The number is higher."
    elif guess > number:
	print "The number is lower."
print "You guessed the number. ", guess
   [/HTML]
I then experimented with random repeatedly and I have not been able to get anything with random to work.  When I went back and tried my original program it now isn't working and I get the following:
[HTML]scott@scott-laptop:~$ python hilow.py
Traceback (most recent call last):
  File "hilow.py", line 4, in <module>
    import random
  File "/home/scott/random.py", line 8, in <module>
    number = random.randrange(0, 5)
AttributeError: 'module' object has no attribute 'randrange'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 38, in apport_excepthook
    from apport.packaging_impl import impl as packaging
  File "/usr/lib/python2.5/site-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.5/site-packages/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/tempfile.py", line 33, in <module>
    from random import Random as _Random
  File "/home/scott/random.py", line 8, in <module>
    number = random.randrange(0, 5)
AttributeError: 'module' object has no attribute 'randrange'

Original exception was:
Traceback (most recent call last):
  File "hilow.py", line 4, in <module>
    import random
  File "/home/scott/random.py", line 8, in <module>
    number = random.randrange(0, 5)
AttributeError: 'module' object has no attribute 'randrange'
scott@scott-laptop:~$ 
[/HTML]
I am not sure whether it is something I am doing wrong or if it is python.  I don't understand this last error.  I appreciate any help you can provide.

---

### Post by Zugzwang on 2008-08-21
Note that the code you posted does not correspond to the error message. Would you please check that both are 100% correct copied&pasted?

---

### Post by WW on 2008-08-21
You created a file called "random.py" in the directory in which you ran your program.  Don't do that; "import random" is reading that file instead of the standard random module.

---

### Post by swappo1 on 2008-08-21
> You created a file called "random.py" in the directory in which you ran your program. Don't do that; "import random" is reading that file instead of the standard random module.
Okay, I didn't realize that was what was happening.  I didn't start having problems until I made the random.py file to experiment with.  After deleting this file everything is working now.  

Does this mean I can't name any files with a function name or does it just matter where the file is saved to?  I am confused on this part since my file was saved in the /home folder.  Thanks for the help.

---

### Post by WW on 2008-08-21
The module search path is explained [here](http://docs.python.org/tut/node8.html#SECTION008120000000000000000).

Are you saying that your random.py was in your home directory, but you were not running hilow.py there?  That's strange, because I don't think your home directory is in the search path by default. (It isn't on my Ubuntu server, nor on my Mac.)

---

### Post by swappo1 on 2008-08-21
No, I saved random.py and hilow.py in my home directory.  If I understand this correctly, since the home directory is where the files are, that would mean the module search path would first start there then search /usr/bin/env python if nothing was found in home?

---

### Post by WW on 2008-08-21
Yes, the search would start in the current directory. If the module was not found there, it would go to the usual python directories (e.g. /usr/lib/python2.5, /usr/lib/python2.5/site-packages, and others). But not "/usr/bin/env python"; that's a command, not a directory. :)

You can see all the directories in the search path by looking at sys.path, e.g. on my Ubuntu server:
```

>>> import sys
>>> sys.path
['', '/usr/lib/python25.zip', '/usr/lib/python2.5', '/usr/lib/python2.5/plat-linux2', '/usr/lib/python2.5/lib-tk', '/usr/lib/python2.5/lib-dynload', '/usr/local/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages', '/usr/lib/python2.5/site-packages/PIL', '/var/lib/python-support/python2.5', '/var/lib/python-support/python2.5/gtk-2.0']
>>> 

```

---

### Post by swappo1 on 2008-08-21
Ok, I understand now.  Thanks for the help.

---

