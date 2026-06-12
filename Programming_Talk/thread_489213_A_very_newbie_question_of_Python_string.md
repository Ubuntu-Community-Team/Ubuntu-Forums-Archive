---
title: "A very newbie question of Python string"
date: 2007-07-01
forum: Programming Talk
---

### Post by mocqueanh on 2007-07-01
Just to know string in Python, but i tried cheating Python, and there is something i dont understand:

[b]
>>> print 'hello ' + '32'
hello 32
[/b]

Okay, but when i type:
[b]
>>> '32' + print 'hello'
SyntaxError: invalid syntax
[/b]

Or:
[b]
>>> x = 32
>>> repr(x) + print " number"
SyntaxError: invalid syntax
[/b]

Why ? I've learning Python, and still a newbie

---

### Post by ssam on 2007-07-01
print must come at the start of a line

you can do

```

>>> print '32' + 'hello'
32hello
>>> x = 32
>>> print repr(x) + " number"
32 number

```

have a look at [http://ubuntuforums.org/showthread.php?t=333867#5](http://ubuntuforums.org/showthread.php?t=333867#5) for some tips on getting started with python

---

### Post by oldmanstan on 2007-07-01
> **mocqueanh said:**
> Why ? I've learning Python, and still a newbie

the reason is that the + operator joins strings or adds numbers but
```
print "hello world"
```
is not a string
```
"hello world"
```
is a string, but when you put print in front of it you are basically calling a function (print) with an argument that happens to be a string ("hello world")

imagine you have a function called foo, you pass a number to foo and it returns a bunch of letters such that
```
foo(23)
```
returns
```
abcd
```

ok, now, if you tried to add 10 to the output of foo...
```
10 + foo(23)
```
you wouldn't get 33, because the ouput of foo(23) is abcd

same with what you're trying to do, the output of print is not a string (i dont think print returns anything since it's a statement rather than a function but i could be wrong, too lazy to look it up but in any case it's not really important here)

in any event, your problem is that you're trying to concatenate things that can't be concatenated.

hope that helps!

EDIT: drat, someone beat me to it, but my response is more convoluted so i win :)

---

### Post by pmasiar on 2007-07-01
> **oldmanstan said:**
> my response is more convoluted so i win :)

Your response is wrong. 32 + foo('hello') has nothing in common with '32" + print 'hello'. print is statement, not function. print will become statement in Py3K, then your convolution will be more relevant :-)

Every statement starts with keyword, what's why line starting with expression (like '32') is wrong.

BTW operator + can do many other tricks: ie can join lists. And you can define your own meaning for it for your own classes by defining __add__() method.

---

### Post by oldmanstan on 2007-07-01
> **pmasiar said:**
> Your response is wrong. 32 + foo('hello') has nothing in common with '32" + print 'hello'. print is statement, not function. print will become statement in Py3K, then your convolution will be more relevant :-)

i note that print is a statement, i was trying to generalize why what he was trying to do is wrong and wouldn't work in other situations either, i assumed that the reason he was trying to do that in the first place was that he figured that since print outputs text, it must BE text :)

---

