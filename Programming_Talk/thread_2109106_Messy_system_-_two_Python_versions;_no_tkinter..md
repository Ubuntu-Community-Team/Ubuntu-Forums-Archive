---
title: "Messy system - two Python versions; no tkinter."
date: 2013-01-26
forum: Programming Talk
---

### Post by zozza on 2013-01-26
I have two versions of Python on my system.

Python 2.6.5 will work from all directories.

Python 3.3.0 will only work from the ~/Python directory.

What I want to do is:
a) remove 2.6.5 and ideally make 3.3.0 work from anywhere and
b) install tkinter for 3.3.0 (for some reason it did not install).

This link explains how to install tkinter ([http://tkinter.unpythonic.net/wiki/How_to_install_Tkinter](http://tkinter.unpythonic.net/wiki/How_to_install_Tkinter)) but it understandably will not install it for 3.3.0 (as it is restricted to one directory).

How can I have one version of Python with tkinter installed?

Thanks!

---

### Post by Bachstelze on 2013-01-26
a) Assuming you are running Ubuntu, you can't. Python 2 is necessary for Ubuntu to run.

How did you install Python 3? You seem to not have done it the standard way.

---

### Post by micahpage on 2013-01-26
If your running a linux distro, it is bad idea to remove python2.x, as there are so many packages that use it. You would break/limit the system. There is no problem with having both versions installed on the same system. However you seemed to install it incorrectly if you only have access to it in one directory.

I have both installed on all my distros. It comes in handy having both as i program in python3 and run other programs in python2, not including repos packages that require python2.

So what distro are you installing it on for curiosity, and what was your process of installation?

---

### Post by zozza on 2013-01-26
When I ran apt-get purge python I saw that it would be impossible to remove version 2.

I am using 10.04.

I would have downloaded 3.3.0 from here: [http://www.python.org/getit/](http://www.python.org/getit/)

whereis python:

python: /usr/bin/python /usr/bin/python2.6-config /usr/bin/python2.6 /etc/python /etc/python2.6 /usr/lib/python3.1 /usr/lib/python2.6 /usr/local/bin/python3.3m-config /usr/local/bin/python3.3-config /usr/local/bin/python3.3 /usr/local/bin/python3.3m /usr/local/lib/python3.3 /usr/local/lib/python2.6 /usr/include/python2.6_d /usr/include/python2.6 /usr/share/python /usr/share/man/man1/python.1.gz

I don't mind running 3.3.0 from the directory but I do need to be able to install tkclient on it.

 File "ex54.py", line 1, in <module>
    from tkinter import *
  File "/home/Python-3.3.0/Lib/tkinter/__init__.py", line 40, in <module>
    import _tkinter # If this fails your Python may not be configured for Tk
ImportError: No module named '_tkinter'

Alternatively, if I downloaded the .tgz file again, and extracted it into a Python 3.3.0 directory, what should I do to make it work globally?

Also:

name@name:~$ python
Python 2.6.5 (r265:79063, Oct  1 2012, 22:07:21) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

But:

name@name:~/Python-3.3$ ./python 
Python 3.3.0 (default, Oct 28 2012, 15:56:01) 
[GCC 4.4.3] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 

Thanks!

---

### Post by micahpage on 2013-01-26
ubuntu should be an easy install for python as its all in the repos

```
sudo apt-get install python3 python3-tk python3-dev
```> /home/Python-3.3.0/Lib/tkinter/__init__.pythat would be why its only known in that directory. It looks like you just extracted the directory into /home and then directly started to try to user tkinter with it.  If so, this is incorrect, and this python3.x is a separate python3.x from you bin python3.x. So installing repos will not effect this. Delete this and install via apt-get.

> ./python try:
```
python3
```in any directory to get the python3.x interpreter

After you install the repos above try the below examples:
```
metulburr@ubuntu:~$ python
Python 2.7.3 (default, Aug  1 2012, 05:14:39) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import Tkinter
>>> exit()
metulburr@ubuntu:~$ python3
Python 3.2.3 (default, Oct 19 2012, 20:10:41) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import tkinter
>>> exit()
metulburr@ubuntu:~$ 

```

---

### Post by trent.josephsen on 2013-01-26
> **micahpage said:**
> If your running a linux distro, it is bad idea to remove python2.x, as there are so many packages that use it.
Minor nit: Not all Linux distros need Python2. Some have already migrated system scripts to Python3 where appropriate. But in general you're more or less right.

---

### Post by micahpage on 2013-01-26
ah, yes true. Arch and Gentoo i know have already 3.x as default.

---

### Post by Bachstelze on 2013-01-26
> **trent.josephsen said:**
> Minor nit: Not all Linux distros need Python2. Some have already migrated system scripts to Python3 where appropriate. But in general you're more or less right.

Others still do not require Python at all.

---

### Post by trent.josephsen on 2013-01-26
Quite right. I actually meant to mention that, but in the course of several revisions...

Python is pretty common though, so I guess you could say "most desktop distros" include one or the other.

---

### Post by zozza on 2013-01-27
Thanks for all your help.

I ran sudo apt-get install python3 python3-tk python3-dev

All seemed to install.

But:

python3
Python 3.3.0 (default, Oct 28 2012, 15:56:01) 
[GCC 4.4.3] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import tkinter
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/local/lib/python3.3/tkinter/__init__.py", line 40, in <module>
    import _tkinter # If this fails your Python may not be configured for Tk
ImportError: No module named '_tkinter'

I tried: sudo apt-get install python python-tk idle python-pmw python-imaging

But:

python is already the newest version.
python-tk is already the newest version.
idle is already the newest version.
python-pmw is already the newest version.
python-imaging is already the newest version.

Anyhow, AIUI, tkinter should be installed along with Python.

However:

python
Python 2.6.5 (r265:79063, Oct  1 2012, 22:07:21) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import Tkinter
>>> exit ()

Any ideas?  Why does Tkinter exist on Python 2 but tkinter not exist on Python3?

---

### Post by zozza on 2013-01-28
anyone?

---

### Post by micahpage on 2013-01-28
to be honest im not sure. The only thing i can think of is you messed up something by installing python3.x manually. 

> I tried: sudo apt-get install python python-tk idle python-pmw python-imagingThose are python2.x

> Anyhow, AIUI, tkinter should be installed along with Python.The only time i ever came across the same error was in Arch Linux where tkinter must be installed as it is not packaged with python. But installing python2.x tkinter repo ```
python-tk
``` and python3.x repo ```
python3-tk
``` fixed that. In Ubuntu, python repos regardless of version, include tkinter. However if you built python yourself, that doesnt mean that it was packaged with tkinter.

> I ran sudo apt-get install python3 python3-tk python3-devSince you first attempted to install via manually:
did you purge python3.x before doing so?  Did you modify any module? Normally when i fix something, i completely remove it and restart from scratch as it is a lot less headache in the end. I would purge python3.x and all its related contents, packages, repos, and restart. AFter everything with python3.x is removed, install it "only" by ubuntu repos.

> Alternatively, if I downloaded the .tgz file again, and extracted it  into a Python 3.3.0 directory, what should I do to make it work  globally?Did you ever extract this into your user library? If so remove this as well. I would remove it regardless of its location, as when you get 3.x working you have no use for it, and will probably get you confused as why some 3rd party modules wont work if you ever use it again.

I found some links relevant though:
[http://stackoverflow.com/questions/5459444/tkinter-python-may-not-be-configured-for-tk](http://stackoverflow.com/questions/5459444/tkinter-python-may-not-be-configured-for-tk)

---

