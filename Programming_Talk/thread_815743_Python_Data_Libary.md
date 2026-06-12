---
title: "Python Data Libary"
date: 2008-06-01
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-06-01
If i were to make a python file (test.py) that were part of a package

i want a statement (function, not and executable script) that, if in test.py, will produce a file that is in the same folder as test.py

to do this i must not put an absolute path, because the package should be movable.

Here is what i want
```

>>> import testpack
>>> testpack.test.func('hello')
>>> exit()

$ls ./testpack/
test.py  test.pyc  hello.txt

```

Hope you understand that

---

### Post by amingv on 2008-06-01
[PHP]file_object = open('hello.txt', 'w') #just plain hello.txt, with nothing else
file_object.write('This is written in the same place where the script is')
file_object.close()[/PHP]

Is that about right?

---

### Post by solarwind on 2008-06-01
Just put a ./ to make the path relative.

---

### Post by Mr.Macdonald on 2008-06-02
yes all that works when you are using a single file or command line. But not if you want it relative to the script you are importing, "key word". try and get the psuedocode from my last post to work

---

### Post by solarwind on 2008-06-02
> **Mr.Macdonald said:**
> yes all that works when you are using a single file or command line. But not if you want it relative to the script you are importing, "key word". try and get the psuedocode from my last post to work

You didn't explain your question properly. I don't get what you're trying to do...

---

### Post by Mr.Macdonald on 2008-06-02
Yeah thats what i guessed.

say i had a folder    ~/testpack/
and in testpack were a file     ~/testpack/test.py
and in testpack their is a function     testpack.test.func()

what would i write in that function to make it, when imported (import testpack.test), open a file in "~/testpack/" and write to it without relative pathing (relative to test.py).


so that i could follow these steps and get these results

```

$cd ~
$python

>>> import testpack.test
>>> testpack.test.func()
>>> exit()

$ls ~/testpack/
test.py   __init__.py   junk.txt

```


I really don't know how to make it clearer that this, Sorry

---

### Post by EXCiD3 on 2008-06-02
So you are saying that...for example, say you import os, you would want it to output in the directory the os module is located?

---

### Post by solarwind on 2008-06-02
> **Mr.Macdonald said:**
> Yeah thats what i guessed.

say i had a folder    ~/testpack/
and in testpack were a file     ~/testpack/test.py
and in testpack their is a function     testpack.test.func()

what would i write in that function to make it, when imported (import testpack.test), open a file in "~/testpack/" and write to it without relative pathing (relative to test.py).


so that i could follow these steps and get these results

```

$cd ~
$python

>>> import testpack.test
>>> testpack.test.func()
>>> exit()

$ls ~/testpack/
test.py   __init__.py   junk.txt

```


I really don't know how to make it clearer that this, Sorry

Well its either relative or absolute paths. I don't get what you want. What does the function do?

---

### Post by stroyan on 2008-06-03
It looks like the inspect module and getabsfile function will give you
what you want.

```

import inspect

def code_directory():
    filename=inspect.getabsfile(code_directory)
    dir=filename[0:filename.rfind('/')]
    return dir

print code_directory()

```

---

### Post by Mr.Macdonald on 2008-06-03
> It looks like the inspect module and getabsfile function will give you
what you want.

```
Code:

import inspect

def code_directory():
    filename=inspect.getabsfile(code_directory)
    dir=filename[0:filename.rfind('/')]
    return dir

print code_directory()
```



I can't test it yet but this looks right, thanks

---

