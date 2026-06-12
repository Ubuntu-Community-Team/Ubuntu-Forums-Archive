---
title: "Python"
date: 2009-06-30
forum: Programming Talk
---

### Post by matmatmat on 2009-06-30
Is there a way to make python recognize "../"
eg:
```

path="../something.html"

``` 
the thing I'm looking for should return something like:
```

/home/user/Documents/something.html

```

EDIT:
Sorry about the title, it was gonna be "Python and '../'" but I forgot to type it

---

### Post by Martin Witte on 2009-06-30
what about
```
martin@sony:~$ python
Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import os.path
>>> print os.path.abspath('../../vmlinuz')
/vmlinuz
>>> 

```

as always: see the [documentation]("http://docs.python.org/library/os.path.html")

---

### Post by sidious1741 on 2009-06-30
I'm not sure exactly what you want but I'm pretty sure you'll find it in os.  If you want to know what '..' is you have to know where you are or where '..' is.

```
>>> os.getcwd() #get current working dir
'/home/timothy'
>>> os.chdir('..') #change current working dir
>>> os.getcwd()
'/home'
```

---

