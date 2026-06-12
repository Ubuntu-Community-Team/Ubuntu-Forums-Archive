---
title: "very simple python question with variables"
date: 2009-05-18
forum: Programming Talk
---

### Post by meg23 on 2009-05-18
I want to be able to nest a command into a variable. For instance:

x = print 'hello'

How do I do this?

---

### Post by Gannon8 on 2009-05-18
You can't.

With python 2.6 and 3.0, print is also a function, so you can do:
```
x = print("Hi")
```

Although I don't see why you would want to do that. I actually have no idea what it would return.

---

### Post by amingv on 2009-05-18
Why would you want to do that?, What do you want to achieve?

Is creating a function, maybe, what you want?

[PHP]>>> def x():
...     print "hi"
... 
>>> x()
hi
>>> 
[/PHP]

---

### Post by Pyro.699 on 2009-05-18
you could try:

```

x = "print 'hello'"
eval(x)

```

---

### Post by Martin Witte on 2009-05-19
> **Pyro.699 said:**
> you could try:

```

x = "print 'hello'"
eval(x)

```

It is actually 'exec' in this case
```
>>> x="print 'hello'"
>>> eval(x)
Traceback (most recent call last):
  File "<pyshell#10>", line 1, in <module>
    eval(x)
  File "<string>", line 1
    print 'hello'
        ^
SyntaxError: invalid syntax
>>> exec(x)
hello

```
eval works like this
```
>>> x = '1 + 2'
>>> eval(x)
3
>>> x  = 'len("hello")'
>>> eval(x)
5
>>> 
```

---

