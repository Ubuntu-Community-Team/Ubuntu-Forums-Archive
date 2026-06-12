---
title: "Learning Python ( Reference:Dive Into Python 5.4 )"
date: 2012-01-11
forum: Programming Talk
---

### Post by nipunshakya on 2012-01-11
Hi. I have started to learn python (most probably an hour ago). I have bit of a knowledge of c-programming, and so i wanted to learn an object oriented one, so i choose python.
within this one hour, i downloaded and installed python, and then began with my first simple program and got error with the following:
```

Python 3.2.2 (default, Sep  4 2011, 09:07:29) [MSC v.1500 64 bit (AMD64)] on win32
Type "copyright", "credits" or "license()" for more information.
>>> 1 + 1
2
>>> print 'hello world
SyntaxError: EOL while scanning string literal
>>> print 'hello world'
SyntaxError: invalid syntax
>>> print "hello world"
SyntaxError: invalid syntax
>>> 

```
i don't know if there has been a drastic change in the syntax from v2 to v3 of python IDLE(which might happen rarely), but i clearly did what was suggested on the book's first example.

Sorry if the question is too simple one, but python is totally new for me. Back in c, i clearly remember that i did just #include<conio> for the printf command.
There was nothing mentioned to do so here...small favor needed here.:)

And forgive for my stupid question please.

Regards, WinuxUser

---

### Post by papibe on 2012-01-11
According to [this]("http://docs.python.org/release/3.0.1/whatsnew/3.0.html"), 'print' is no longer an statement but a function now (v3.0 and up).

This should work:
```
print("hello world")
```
Hope it helps.
Regards.

---

### Post by nipunshakya on 2012-01-12
it surely helped. should have read the documentation too...thanks

---

