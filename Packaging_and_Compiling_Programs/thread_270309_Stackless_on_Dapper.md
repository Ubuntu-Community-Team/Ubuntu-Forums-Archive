---
title: "Stackless on Dapper"
date: 2006-10-03
forum: Packaging and Compiling Programs
---

### Post by goofyheadedpunk on 2006-10-03
I'm attempting to compile stackless python as pulled via ```
svn checkout http://svn.python.org/projects/stackless/Python-2.4.3/dev/
``` but am having a terrible time of it. I've pulled the dependancies for python2.4 and have installed python-dev and issue the standard ./configure && make && sudo checkinstall but am often thrown by this or that. One moment IDLE won't exists stopping my install a file that exists doesn't meaning the build process can't change it's permissions.

So, it seems I don't know what I'm doing. 

I'd like to drop stackless in the place of CPython so I can play with what looks to be a really cool toy. However the normal compile, install and pray process seems to not work. Is there anyone using stackless instead of Debian's default CPython? What did you do?

---

### Post by maubp on 2006-10-05
Maybe you should install stackless python somewhere else using the ./configure prefix argument (maybe under your home directory - that way you can't screw up the system CPython installation.

---

