---
title: "pyOgre - help setting it up"
date: 2007-06-23
forum: Programming Talk
---

### Post by Choad on 2007-06-23
ok i compiled ogre from source because pyOgre required the latest version. that went ok. then i set up pyOgre 

python setup.py build
sudo python setup.py install

and that seemed to go fine however

```

richard@richard-laptop:~$ python
Python 2.5.1 (r251:54863, May  2 2007, 16:56:35) 
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import ogre.renderer.OGRE as ogre
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python2.5/site-packages/ogre/renderer/OGRE/__init__.py", line 8, in <module>
    from _ogre_ import *
ImportError: No module named _ogre_
>>> 

```

hmmmm???

also...

[img]http://img485.imageshack.us/img485/4962/screenshotogrefilebrowstm6.png[/img] 
i followed the path and i do have stuff there. seems to have installed properly, it just cant find the module. do i have to update environment variables or something?

---

### Post by Choad on 2007-06-24
bump

anyone??

---

### Post by Choad on 2007-06-24
bump bump bump

---

### Post by Choad on 2007-06-25
bump

:'(

---

### Post by skullmunky on 2007-06-26
i don't have an answer but i want to know too.  i'm brand new to python but maybe there's another module missing (_ogre_).   which makes me think ogre.renderer.OGRE is one thing, and then there's an underlying module called _ogre_.  what do the ogre forums say?  please post if you get a solution because i know i'll be hitting this one in about 2 weeks.

---

### Post by Choad on 2007-06-27
bumppppppppp

---

### Post by poo_22 on 2011-01-02
I am having the same issue as OP. Sorry to dig this thread up but can anyone help?

---

### Post by lakersforce on 2012-02-22
I'm having this problem too!

---

