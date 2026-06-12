---
title: "Python Socket Problem ..."
date: 2007-06-04
forum: Programming Talk
---

### Post by A.I. BOT on 2007-06-04
It was working perfectly today, dident touch it at all, then I came back a few hours later and ran the program and got an error.

```
tyler@tyler-laptop:~$ python chat.py
Traceback (most recent call last):
  File "chat.py", line 1, in <module>
    from socket import socket, gethostbyname, AF_INET, SOCK_STREAM;
  File "/usr/lib/python2.5/socket.py", line 5, in <module>
    This module provides socket operations and some related functions.
AttributeError: 'module' object has no attribute 'AF_INET'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 38, in apport_excepthook
    from apport.fileutils import likely_packaged
  File "/var/lib/python-support/python2.5/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/var/lib/python-support/python2.5/apport/report.py", line 14, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os, sys
  File "/usr/lib/python2.5/urllib.py", line 26, in <module>
    import socket
  File "/usr/lib/python2.5/socket.py", line 5, in <module>
    This module provides socket operations and some related functions.
AttributeError: 'module' object has no attribute 'AF_INET'

Original exception was:
Traceback (most recent call last):
  File "chat.py", line 1, in <module>
    from socket import socket, gethostbyname, AF_INET, SOCK_STREAM;
  File "/usr/lib/python2.5/socket.py", line 5, in <module>
    This module provides socket operations and some related functions.
AttributeError: 'module' object has no attribute 'AF_INET'

```

Any idea how to fix this :S, I dont understand why it would randomly stop working?

Thanks.

---

### Post by ghostdog74 on 2007-06-05
you did a "from socket ....import ....." then after that you did a "import socket"...
why don't you do everything with just one import. ie, import socket
for not confusing your namespaces, best practice is to use  the import <module> way, than the "from <module> import " method.

---

### Post by AdamG on 2007-06-05
Can you check if you have a /usr/lib/python2.5/lib-dynload/_socket.so file?

That seems t be where the AF_INET descriptor originates from. 

Your imports, BTW, are more or less OK. Some situations call for import bar, and some situations call for from foo import bar. Some even call for import foo.bar as bar. [Different tasks call for different conventions]("http://xkcd.com/c163.html"). 

With a problem like this one, I'd try importing * just to see what happens.

---

### Post by A.I. BOT on 2007-06-05
@ghostdog74: Tried your suggestion, same error :(
@AdamG: Yes I have that file, also tried your import suggestion and get the same error.

Thanks.

---

### Post by ghostdog74 on 2007-06-05
> **A.I. BOT said:**
> @ghostdog74: Tried your suggestion, same error :( 
don't mean to sound skeptic, but you used import socket method right? did you change your quantifiers? meaning , if originally you have say, gethostbyname() , then did you change it to socket.gethostbyname()???

---

### Post by AdamG on 2007-06-05
If we could see source, that would be great. Try to get as small a test case as possible that fails. 

Does a script that has only "from socket import AF_INET" fail?

---

### Post by A.I. BOT on 2007-06-05
I found the problem, for some reason I cant run the socket code from my home folder so i moved it into a new folder and it worked fine.

Thanks for the help. :D

---

### Post by karlw on 2008-10-26
Why could he not execute this from his home dir?  Could anyone shed some light on this?

---

### Post by unutbu on 2008-10-26
When you run a python script, the directory that contains the script is added to the front of sys.path.
sys.path is a list of all the directories that is searched for modules. 

So my guess is that he had a file in his home directory (perhaps something like socket.py) 
which conflicted with a standard module. So when he tried to import socket, he was getting his local copy instead of the standard library module.

To see how sys.path works, run this script
```

#!/usr/bin/env python
import sys
print sys.path
```
Move the script to various directories and see the difference.

---

### Post by karlw on 2008-10-26
You hit that one out of the park!  I had the same problem as him, cannot execute in the home directory, I figured it was some permission thing, but I had a socket.py setting in my home dir.

Many Thanks!

---

### Post by bruno386 on 2011-12-19
wow i had the same problem, great guess on "socket.py" :)

---

