---
title: "Python Printing"
date: 2009-11-01
forum: Programming Talk
---

### Post by DBQ on 2009-11-01
Hi everybody. I am new to Python. I am trying to print something but having trouble printing it correctly:

```

MSG1 = "Hello"
MSG2 = "World"
print MSG1 + " " + MSG2

```

Hello World as expected with a newline in the end.  I want to print "Hello World" without the newline. When I try to do this:

```

MSG1 = "Hello"
MSG2 = "World"
print MSG1 + " " + MSG2,

```

i.e. adding comma at the end of the print statement, nothing is printed at all.  What I am doing wrong?  Thank you all for your help.

---

### Post by 0cton on 2009-11-01
If you would like to provide what output you want It would be helpful.
And also in python print is a statement and AFAIK (maybe not in python 3.0) it will automatically call a newline.
Still you could still manage to get the output you want.
also the coma at the end is not valid
try + "\b" (not guaranteed to work and very ugly) (\b=backspace)
also guess you will have to live with it heh?
if you mean you want to print just hello world and not hello world\n AFAIK it's not possible prior to 3.0 with python Standard library (but I may be wrong as I never really needed to think about it heh, never had to "use" it heh)

---

### Post by DBQ on 2009-11-01
This is sad that such simple functionality is missing.

---

### Post by diesch on 2009-11-01
Works here as expected (I'm adding another print to show the (missing) newline:

```

Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> MSG1 = "Hello"
>>> MSG2 = "World"
>>> print MSG1 + " " + MSG2; print '*'*20
Hello World
********************
>>> print MSG1 + " " + MSG2,; print '*'*20
Hello World ********************

```

If you run the code using some IDE the IDE may buffer the output until the next newline.

Note that you can just use
```
print MSG1, MSG2, 
``` instead of ```
print MSG1 + " " + MSG2,
```

---

### Post by 0cton on 2009-11-01
but you just gave an example of a very simple program.
bet more precise on what type of output you need and someone/I'll tell you how to do it (maybe :P )
I really don't see what you tried to achieve with that sample program of yours
just print "hello world" would do
edit: I stand corrected it is possible I just never needed to use that in python anyway :P

---

### Post by eightmillion on 2009-11-01
There's no functionality missing here. You just have to go about a different way. Specifically, by using sys.stdout.

[PHP]>>> import sys
>>> MSG1 = "Hello"
>>> MSG2 = "World"
>>> sys.stdout.write(MSG1 + " " + MSG2)
Hello World>>> sys.stdout.write(MSG1 + " " + MSG2 + "\n")
Hello World
>>>[/PHP]

---

### Post by Can+~ on 2009-11-01
[PHP]>>> MSG1 = "Hello"
>>> MSG2 = "World"
>>> print MSG1 + " " + MSG2,
Hello World
[/PHP]

Not sure what's wrong. The interactive shell always appends a "\n", but on a normal script this doesn't happen.

For example, you can compare this two results:

[PHP]>>> for i in xrange(0, 10):
...     print i
... 
0
1
2
3
4
5
6
7
8
9
>>> for i in xrange(0, 10):
...     print i,
... 
0 1 2 3 4 5 6 7 8 9[/PHP]

Python 3:
[PHP]>>> for i in range(0, 10):
...     print(i, end=" ")
... 
0 1 2 3 4 5 6 7 8 9 >>>[/PHP]

---

