---
title: "reading dive into python.. getting weird output from the example programs.."
date: 2007-05-01
forum: Programming Talk
---

### Post by billdotson on 2007-05-01
I did the following: 

```

>>> import odbchelper
>>> params = {"server":"mpilgrim", "database":"master", "uid":"sa", "pwd":"secret"}
>>> print odbchelper.buildConnectionString(params)
server=mpilgrim;uid=sa;database=master;pwd=secret
>>> print odbchelper.buildConnectionString.__doc__

``` and my output has the server:mpilgrim and all those word in reverse order.  I am using python 2.5

---

### Post by Jessehk on 2007-05-01
I don't know if this is the answer to your question (it was a bit unclear), but I'll hope for the best. :)

An important point about dicts in Python (and similar structures in other languages such as Hashes in Ruby) is that they are unordered.

For example, see this commented python session:
```

Python 2.5.1 (r251:54863, Apr 19 2007, 11:03:39) 
[GCC 4.1.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> # create a new dict object named "d"
... d = {}
>>> # add a few pairs to d
... d["Joe"] = 20 # Joe is 20 years old
>>> d["Jane"] = 30
>>> d["Joseph"] = 40
>>> d
{'Jane': 30, 'Joseph': 40, 'Joe': 20}
>>> 

```

Notice that the items in the dict are not in the same order as you created them, just that the data you set is still intact (Joe is still 20, Jane is still 30, etc).

---

### Post by AdamG on 2007-05-02
Yup, Jessehk is right - dicts aren't ordered. That's OK, because you'll never need to access a dict via "first element" or anything like that - you just provide a key, and it'll provide the value.

---

