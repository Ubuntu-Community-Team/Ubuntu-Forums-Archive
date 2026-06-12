---
title: "Sorting lists in python where 10 comes after 9."
date: 2013-02-09
forum: Programming Talk
---

### Post by jsmidt on 2013-02-09
Hey everyone.  I have a list in python like:

```
['file-1', 'file-9', 'file-2', 'file-10']
```

When I try and sort this list I get the sorting that you would get if you typed ls in a unix directory:

```
['file-1', 'file-10', 'file-2', 'file-9']
```

where 10 comes after 1 but before 2.  I would like to sort this list such that 10 comes after 9 like:

```
['file-1', 'file-2', 'file-9', 'file-10']
```

Is there a simple way to do this with python?  Thanks.

---

### Post by JDShu on 2013-02-09
Crappy solution that works:

```
sorted(['file-1', 'file-9', 'file-2', 'file-10'], key=lambda s: int(s[5:]))
```[http://wiki.python.org/moin/HowTo/Sorting](http://wiki.python.org/moin/HowTo/Sorting) <- go here for details.

EDIT : Answer below is better :P

---

### Post by Vaphell on 2013-02-09
there is a way, but not necessarily simple. You have to plug your own sorting rule into the stock sorting (define what to do with the value to get the sorting key).

simple example of the concept where the values are sorted by 2nd part of the string cast to integer
```
>>> l = [ 'a-1', 'a-2', 'a-11' ]
>>> sorted( l, key=lambda a: int(a.split("-")[1]) )
['a-1', 'a-2', 'a-11']
```

more suitable solutions from google
[http://stackoverflow.com/questions/4836710/does-python-have-a-built-in-function-for-string-natural-sort](http://stackoverflow.com/questions/4836710/does-python-have-a-built-in-function-for-string-natural-sort)

if you process real files and are in control of their names, do yourself a favor and pad them with 0s to fixed width so even standard alphanumeric sorting returns correct order.

---

### Post by jsmidt on 2013-02-10
Thanks a lot guys.

---

