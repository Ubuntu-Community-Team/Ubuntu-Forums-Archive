---
title: "Finding &amp; Defining the PYTHONPATH"
date: 2007-08-08
forum: Programming Talk
---

### Post by Wolfraptor1 on 2007-08-08
Alright, here's my question. In order to import modules, someone whom I thank greatly, told me to find and modify the PYTHONPATH file; the problem is, I don't even begin to known the commands in the python interpreter to even begin that, can someone help?

---

### Post by pmasiar on 2007-08-08
on ubuntu? all is set up.

To try, check [how to start](http://learnpython.pbwiki.com/HowToStart) page.

In short: At command propmt, type:

> python

(python shell will start, with >>>)
>>> import cgi
If no error messages, you are in. If not, post massages here.

---

### Post by vambo on 2007-08-08
Put this in your .basgrc

```
export PYTHONPATH=$PYTHONPATH:<my pythonpath>
```

Where <my pythonpath is, for example /home/user_name/python_files
Where python_files is the directory containing the .py files you want to import

Cheers

---

### Post by 5463 on 2008-02-18
Make a backup of the file:  .profile
then add this line to the file:   .profile

export PYTHONPATH=/home/steve/Documents

if your username=steve
and the directory you want added is /home/steve/Documents

On the other hand, if the username=Frank
and you want to add the Music directory
then add this line to the file:  .profile

export PYTHONPATH=/home/Frank/Music

Also, note that the file (.profile) is a hidden file.
You may have to click on VIEW then SHOW HIDDEN FILES
within Nautilus to access hidden files.
Also, the file:  .profile  is found in the Home Folder

Reference Links:
[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)
[http://docs.python.org/lib/module-sys.html](http://docs.python.org/lib/module-sys.html)
[http://ubuntuforums.org/showthread.php?t=2793](http://ubuntuforums.org/showthread.php?t=2793)

peace

---

### Post by dwblas on 2008-02-19
It is normally done in the program itself.  Directories added to the $PYTHONPATH variable  are ones that you access all of the time.

import sys
sys.path.append("/path_to/module/")
import the_program   ## can now be found in the dir /path_to/module/

---

