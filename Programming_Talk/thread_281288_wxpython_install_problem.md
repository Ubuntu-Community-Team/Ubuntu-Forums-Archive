---
title: "wxpython install problem"
date: 2006-10-20
forum: Programming Talk
---

### Post by mwthrane on 2006-10-20
Hi

Ive run thru some basics around python succesfully. I didnt find it too hard so i wanted to try something harder and wanted to install wxpython. I installed it via apt-get. But for some reason it put the files in Python 2.4 dir, and im using Python 2.5. So i moved the files from python2.4 site-packages to 2.5 site-packages. 

Before i did that i got could not load wxpython module.

Now im getting:
$ python test.py
Traceback (most recent call last):
  File "test.py", line 1, in <module>
    import wx
  File "/usr/local/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/__init__.py", line 42, in <module>
    from wx._core import *
  File "/usr/local/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 4, in <module>
    import _core_
ImportError: /usr/local/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/_core_.so: undefined symbol: PyUnicodeUCS4_FromEncodedObject

How to fix this so i can use wxpython.
Alternatively if this wont work, how can i revert back and use python 2.4. It would probably work under 2.4.
So when i type python in terminal it tells me im using 2.4. Now it obviously says 2.5.

Thanks in advance.

---

### Post by junglepeanut on 2006-10-21
You can just say python2.4 instead of python.

I would like to mention my 2.5 also does not work with qt. All other versions are happy (in Edgy.)

---

### Post by mwthrane on 2006-10-21
Very nice that works. Tho its abit annoying having to type 2.4. Is it to do so when i type python it start python 2.4?

---

### Post by junglepeanut on 2006-10-22
You could just make the file a script if you want with the bash bang command that way all you have to type is the file name.

i.e. in the file "test"
```

#!/usr/bin/python2.4

print 'hello'
```

then at cli
```

test
```
or
```
./test
```
depending on your path.

---

