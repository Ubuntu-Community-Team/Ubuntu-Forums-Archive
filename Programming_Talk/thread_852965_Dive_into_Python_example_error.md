---
title: "Dive into Python example error ?"
date: 2008-07-08
forum: Programming Talk
---

### Post by visualreactor on 2008-07-08
Hello,
I am learning python by reading [Dive into Python]("http://www.diveintopython.org") by Mark Pilgrim. I was reading [chapter 5 - Objects and Object Orientation]("http://www.diveintopython.org/object_oriented_framework/index.html") and I am kind of stuck with example [5.11]("http://www.diveintopython.org/object_oriented_framework/userdict.html") and example [5.12]("http://www.diveintopython.org/object_oriented_framework/special_class_methods.html").

According to the examples FileInfo class has been defined as :
```

class FileInfo(dict):                  
    "store file metadata"
    def __init__(self, filename=None): 
        self["name"] = filename

```
and then the following function is added :
```
def __getitem__(self, key): return self.data[key]
```

But am I missing something here ? I ran the code & to confirm my initial doubts - it gives an error because FileInfo does not contain a data member called data. Is this a mistake or have I made an error somewhere ?

I tried rewriting the FileInfo class (up until that section only) as follows :

```
class FileInfo(dict):
    "Display file metadata"
    def __init__(self, filename=None):
        self.data = {}
        self.data["name"] = filename
    def __getitem__(self, key = None):
        if key is not None:
            return self.data[key]
        return self.data
```

What is not working is if I try just instantiating an object of FileInfo type say 'test' and just hitting test in the interpreter - it returns and empty dictionary. Is that how the functionality is supposed to be when you define the __getitem__ sepecial function ? Shouldn't it return the entire dictionary if I just enter 'test' in the interpreter ?

Rohit Arondekar
[www.visualreactor.org](www.visualreactor.org)

---

### Post by ghostdog74 on 2008-07-08
i would recommend learning Python from the official Python tutorial. Dive into Python is quite dated.

---

### Post by rikxik on 2008-07-08
I don't think __getitem__() gets called if you simply type the name in the interpreter:

```

>>> t = {'a': 1, 'b': 2}
>>> t.__str__()
"{'a': 1, 'b': 2}"
>>> t.__repr__()
"{'a': 1, 'b': 2}"
>>> t.__getitem__('a')
1
>>> t.__getitem__()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: __getitem__() takes exactly one argument (0 given)

```

Maybe you need to check __repr__?

---

### Post by visualreactor on 2008-07-08
rikxik ~ That does shed some light.

I actually liked Dive into Python - however if there are mistakes then I guess I will have to switch over to the official tutorial and docs. So the main question is - is the example wrong ? Because if it is then shouldn't someone notify the author to correct the mistake ?

---

### Post by pmasiar on 2008-07-08
> **visualreactor said:**
> is the example wrong ? Because if it is then shouldn't someone notify the author to correct the mistake ?

if it looks wrong, and maybe it's **you** who should notify author? :-)

Seems like you are experienced programmer (just new to Python). Try Guido's tutorial. Also, you may compare explanations in free e-books linked in wiki in my sig (even if wiki is more for beginners).

---

### Post by dtmilano on 2008-07-08
Actually you don't need __getitem__ if you are extending dict.

```
#! /usr/bin/env python

class FileInfo(dict):
        "store file metadata"
        def __init__(self, filename=None):
                self["name"] = filename

        #def __getitem__(self, key):
        #       return self[key]

if __name__ == "__main__":
        f = FileInfo("foo")
        print f
        print f["name"]
        f["genre"] = 31
        print f

```

gives

> {'name': 'foo'}
foo
{'genre': 31, 'name': 'foo'}


---

### Post by visualreactor on 2008-07-08
pmasiar ~ I am not an experienced programmer actually rather a beginner. So I just wanted to confirm that it was a mistake in the example.

I'll send him a mail now.

Thanks for all the help and pmasiar, your wiki is awesome I've already bookmarked it. :)

---

### Post by pmasiar on 2008-07-08
If you are beginner, don't dive: learn to swim first! :-)

With python (unlike Java), you don't even have to start with objects and OOP until well past beginner stage. Use system object but don't worry about creating your own - use dicts and be happy.

---

