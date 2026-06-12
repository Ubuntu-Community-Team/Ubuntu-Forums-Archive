---
title: "[SOLVED] how to return a line in python interp"
date: 2008-12-27
forum: Programming Talk
---

### Post by SonnHalter on 2008-12-27
i want to move down a line. but it just runs the code when i hit enter. helP?

---

### Post by nvteighen on 2008-12-28
> **SonnHalter said:**
> i want to move down a line. but it just runs the code when i hit enter. helP?

Well, the idea of an interpreter is that you get an immediate result of the command you entered... In the days of QBASIC, the interpreter was called the "Immediate" window for that reason...

You have two possiblities: either create a function and execute it or create a .py file with the code you want.

---

### Post by iQuizzle on 2008-12-28
use teh backslash!

print 'use teh \
        backslash!'

---

### Post by SonnHalter on 2008-12-28
> **nvteighen said:**
> Well, the idea of an interpreter is that you get an immediate result of the command you entered... In the days of QBASIC, the interpreter was called the "Immediate" window for that reason...

You have two possiblities: either create a function and execute it or create a .py file with the code you want.

w8, so what would i use if i wanted to write a multi-line code?

---

### Post by nvteighen on 2008-12-28
In the interpreter:
```

ugi@UGI:~$ python
Python 2.5.2 (r252:60911, Nov 14 2008, 19:46:32) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> def multiline(arg):
...     myvar = arg * 2
...     
...     if myvar == 10:
...             print "AAA!"
...     else:
...             print "BBB!"
... 
>>> multiline(15)
BBB!
>>> multiline(5)
AAA!
>>> 

```

**def** introduces functions in Python. But anyway, the interpreter is meant for playing with the language or testing small pieces of code, never for development. For that, you write files and then run them using **python <filename>** at the terminal.

---

### Post by SonnHalter on 2008-12-28
so to write  a python file would i just write in the text editor and then save as py?

---

### Post by nvteighen on 2008-12-28
> **SonnHalter said:**
> so to write  a python file would i just write in the text editor and then save as py?
Exactly :)

---

