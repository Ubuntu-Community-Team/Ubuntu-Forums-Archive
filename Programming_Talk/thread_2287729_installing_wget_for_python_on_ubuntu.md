---
title: "installing wget for python on ubuntu"
date: 2015-07-21
forum: Programming Talk
---

### Post by huff2 on 2015-07-21
Hi all,

I want to use the wget library in python so I downloaded the .tar.gz file, extracted it and went to the file path with the setup.py file and tried ./setup.py and python setup.py but can't get it to work. I get errors. 

```
 [FONT=monospace][COLOR=#000000]brandon@brandon-NV57H:~/Downloads/wget-2.2$ ./setup.py [/COLOR]
from: can't read /var/mail/distutils.core 
./setup.py: line 4: syntax error near unexpected token `(
' 
./setup.py: line 4: `def get_version(relpath):'


[/FONT] [FONT=monospace][COLOR=#000000]brandon@brandon-NV57H:~/Downloads/wget-2.2$ python setup.[/COLOR]
py 
usage: setup.py [global_opts] cmd1 [cmd1_opts] [cmd2 [cmd
2_opts] ...] 
   or: setup.py --help [cmd1 cmd2 ...] 
   or: setup.py --help-commands 
   or: setup.py cmd --help 

error: no commands supplied

[/FONT]
[FONT=monospace][/FONT]

```

Can anyone help me get this up and running? I'm using python 2.7

---

### Post by CantankRus on 2015-07-21
Try installing with pip.
```
sudo apt-get install python-pip
```
```
sudo pip install wget
```

---

### Post by huff2 on 2015-07-21
Thanks, it worked. But, what exactly did all of that do. What is pip? can you break it all down for me. Thanks :)

---

### Post by huff2 on 2015-07-21
One tiny problem though. I'm still unable to import with python

> import wget

---

### Post by CantankRus on 2015-07-21
Maybe you just needed sudo to run the command in your first post.
> _python-pip_
pip is a replacement for easy_install, and is intended to be an improved
Python package installer.  It integrates with virtualenv, doesn't do
partial installs, can save package state for replaying, can install from
non-egg sources, and can install from version control repositories.
Sorry I don't code... just use pip to install a couple of python scripts I use.
pip allows you to search, install and upgrade python packages from [**_[COLOR="#B22222"]Python Package Index[/COLOR]_**]("https://python-packaging-user-guide.readthedocs.org/en/latest/glossary.html#term-python-package-index-pypi")

Best I can do is give you a link... [**_[COLOR="#B22222"]Installation Tool Recommendations[/COLOR]_**]("https://python-packaging-user-guide.readthedocs.org/en/latest/current.html")

Maybe start a new thread in [**_[COLOR="#B22222"]Programming Talk[/COLOR]_**]("http://ubuntuforums.org/forumdisplay.php?f=39")

---

### Post by huff2 on 2015-07-21
thanks!

---

### Post by huff2 on 2015-07-21
Hi all,

I'm trying to use wget in one of my programs. I used pip to install wget and it said that the installation was successful but the problem is that I still can't import wget. Can anyone help? I'm using python2.7.

---

### Post by Bucky Ball on 2015-07-21
*Thread merged*.

Please do not post duplicates on the same issue. You are getting support here already. The advice to start a new thread in ***Programming Talk*** was not good. It dilutes your chances of support as your support request hasn't changed, just progressed a little. 

You are already in ***Programming Talk***. Thanks.

---

### Post by mystics on 2015-07-22
Try checking */usr/local/lib/python2.7/dist-packages/* to make sure that wget.py and wget.pyc are there. There should also be a wget-related directory there. If they're not there, then you'll need to redo the pip install. If they are there, what errors are you getting when you try to import it?

Also, is there any reason you are trying to use wget rather than Python's [urllib2]("https://docs.python.org/2/library/urllib2.html")?

---

