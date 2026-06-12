---
title: "new to python.. help needed"
date: 2006-01-14
forum: Programming Talk
---

### Post by wizzkid on 2006-01-14
I follow this this site [http://www.arson-network.com/index.php?class=tutorial&subargs=430](http://www.arson-network.com/index.php?class=tutorial&subargs=430)

im not sure if I have these:
   Python = installed as defaul. .2.4
   GTK 
   Glade = installed
   pyGTK
   pyGlade 
the other im not sure.. how to check. 

But I followed and created the program. but I encounter error upon running ./swap.py

Error is:
(swap.py:11343): Gdk-WARNING **: locale not supported by Xlib

(swap.py:11343): Gdk-WARNING **: cannot set locale modifiers
Traceback (most recent call last):
  File "./swap.py", line 69, in ?
    app=gui() #9
  File "./swap.py", line 39, in __init__
    dic = {"on_swap_clicked" :      #2
AttributeError: gui instance has no attribute 'on_swap_clicked'

I've attached the tar.gz file which contains the cource code..

Sorry. Im a newbie that want to learn programming. this is my first step in python

thanks

---

### Post by ow50 on 2006-01-14
You have an indentation error.

Line
```
def on_swap_clicked(self,widget):
```
needs to be indented to the same level as
```
def __init__(self):
```

The indentation must look like
```

class SomeClass(object):
    def __init__(self):
        self.some_attr = None
    def some_method(self):
        print 'Doing some method.'

def some_function():
    print 'This is not a SomeClass method.'

```

---

### Post by wizzkid on 2006-01-15
hmmmmmm, yeh it worked! its so sensitive ah! hmmm,, THANKS! :)

can somebody point me where to find an ebook for python? something like basic in python.. I tried to look a book for python in the bookstore but I couldnt find t.

Thanks a lot

---

### Post by GazaM on 2006-01-15
The two best free online Python books are, in my opinion, [byte of python]("http://www.byteofpython.info/") and [dive into python]("http://diveintopython.org/"). Both can be downloaded in a variety of formats and languages, or read online. Byte of python is more beginner oriented, but dive into python is more in-depth and goes into more commonly used modules, not just stuff included with Python itself.... I found it very helpful when learning XML parsing.

Anyway, good luck with Python. It's a great programming language.

---

### Post by wizzkid on 2006-01-15
Thanks a lot .. will read and go thru it :) really appreciate your help! :)

---

