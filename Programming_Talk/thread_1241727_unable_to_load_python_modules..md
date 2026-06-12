---
title: "unable to load python modules."
date: 2009-08-16
forum: Programming Talk
---

### Post by zay2 on 2009-08-16
Hello

i wanted to test stackless python and installed stackless 2.6.2. Then i found that django projects did not run anymore because system(?) was unable to load mod_python for apache. 

so i installed mod_wsgi and now everything fails when it tries to load MySQLdb. 

When installing stackless python i followed some example where it suggested that when installing stackless python you install it to some other directory than the one where python originally is. So i installed stackless into /lib/local

when i type python in prompt and import sys and print out sys.path i get this info :
>>> print sys.path
['', '/usr/local/lib/python26.zip', '/usr/local/lib/python2.6', '/usr/local/lib/python2.6/plat-linux2', '/usr/local/lib/python2.6/lib-tk', '/usr/local/lib/python2.6/lib-old', '/usr/local/lib/python2.6/lib-dynload', '/usr/local/lib/python2.6/site-packages']

What do i have to do to get all modules working with stackless python?

I did find this article where they have similar problem (if i understood it correctly). Can anyone translate this symlinking for me? What do i have to do to? beeing a linux newbie i don't think i can figure this out on my own.

Alan

---

