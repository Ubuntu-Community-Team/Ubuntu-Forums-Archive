---
title: "Popen compatibility Linux and Windows"
date: 2011-07-03
forum: Programming Talk
---

### Post by bcz on 2011-07-03
I use subprocess.Popen to load program prog1 successfully with Linux


from subprocess import Popen

...

Popen('',executable='./prog1')


Trying this under windows, the I find it does not work

Neither does  Popen('',executable='c:\\progDir\\prog1')

or Popen('',executable='c:\\python27\\python.exe c:\\progdir\\prog1.py')

My rationale for using Popen is that it will handle platform dependancies for me.  Any suggestions or pointers to useful information in this area

Rgds Bill

---

### Post by bcz on 2011-07-03
The following works

Popen('c:\python27\python.exe prog1');

However python scripts must have a .py extention to load from an explorer panel.  Dont expect this to change.

Popen will not automatically load python to run a python script.  I feel that this could be automated..  Hell who expects perfection on Windows

---

### Post by nvteighen on 2011-07-04
The problem is that popen is part of the POSIX API, which is for UNIX(-like) systems. So it assumes a POSIX system, which Windows is not.

Python incorporates the POSIX calls and implements them for Windows, so that you can port a Python script to that OS more easily, but the problem is that you have to take account of Windows's specific behaivor, like the one you've encountered.

If you know how to do it, I'd suggest you to modify the second script in order that you can import it instead of executing it through another process.

---

