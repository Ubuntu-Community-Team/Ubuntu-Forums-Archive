---
title: "Python - SyntaxError: invalid syntax"
date: 2010-10-06
forum: Programming Talk
---

### Post by vim_lover on 2010-10-06
```
cats=['Tom','Snappy','Kitty','Jessie','Chester']
print cats [2]
``````
:~$ python cats.py
  File "cats.py", line 2
    print cats [2]
             ^
SyntaxError: invalid syntax
```

---

### Post by Tony Flury on 2010-10-06
Did you try removing the space infront of the "[" ?

Also if you are using python v3 (not sure) then print is a function, and AFAIK needs brackets  
:
```

print( cats[2])

```

---

### Post by vim_lover on 2010-10-06
Thanks Tony Flury,
```
print( cats[2])
```Removing spaces didn't work.  After enclosing the arguments to print in brackets it worked.  I am using python 3.1.2

---

### Post by Tony Flury on 2010-10-06
[http://docs.python.org/py3k/](http://docs.python.org/py3k/)

The above link is the Python 3 documentation.

As a matter of interest why did you choose python 3 - as I understand most code under Linux is still Python 2 and Python 3 is still under development and therefore does not have the full range of support of toolkits and libraries (this is what i have heard - some or all of these maybe be incorrect or historic).

---

