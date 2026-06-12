---
title: "Ubuntu Quickly error?"
date: 2013-04-25
forum: Programming Talk
---

### Post by tubunu on 2013-04-25
Whenever I create a new project 
```
quickly create ubuntu-application test-project
```
and then want to edit the text file
```

cd test-project 
quickly edit
```

I get this error: 
```
$ quickly edit
Traceback (most recent call last):
  File "/usr/share/quickly/templates/ubuntu-application/edit.py", line 73, in <module>
    instance = subprocess.Popen([editor] + filelist, stderr=nullfile)
  File "/usr/lib/python2.7/subprocess.py", line 679, in __init__
    errread, errwrite)
  File "/usr/lib/python2.7/subprocess.py", line 1249, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory
ERROR: edit command failed
Aborting

```

I don't know what I'm doing wrong.

---

### Post by michi2 on 2014-03-03
Hi... One year later (sorry) but maybe somebody has the same issue.
**quickly edit** just open de editor **gedit** with all the python scripts. May be you don't have gedit installed?

---

### Post by mj.marches on 2014-12-13
Thanks ver much. i was using Lubuntu and did not realize that gedit was not installed. Lubuntu quickly error with 'quickly edit'. 'quickly edit' uses gedit.

---

