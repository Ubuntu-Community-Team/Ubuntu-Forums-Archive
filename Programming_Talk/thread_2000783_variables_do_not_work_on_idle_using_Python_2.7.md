---
title: "variables do not work on idle using Python 2.7"
date: 2012-06-10
forum: Programming Talk
---

### Post by Dav14 on 2012-06-10
Hey, I regonized that Variables do not  work in funktions on Idle using Python2.7.

An example:

I define posit with raw_input, but if I want to print posit out, there an red mistake message

>>> def quest_posit ():
    posit = raw_input("What do you want? ")

    
>>> quest_posit ()
What do you want? an answer

>>> print (posit)
Traceback (most recent call last):
  File "<pyshell#13>", line 1, in <module>
    print (posit)
NameError: name 'posit' is not defined


What can I do ???

help would e really nice

---

### Post by Bachstelze on 2012-06-10
When you define a variable inside a function, that variable is local to the function and cannot be accessed outside of it. This is not specific to Python, by the way, virtually all imperative languages work like that. What you can do is

```
>>> def quest():
...     s = raw_input("? ")
...     return s
... 
>>> foo = quest()
? blah
>>> print foo
blah

```

---

### Post by Tony Flury on 2012-06-10
> **Dav14 said:**
> Hey, I regonized that Variables do not  work in funktions on Idle using Python2.7.

An example:

I define posit with raw_input, but if I want to print posit out, there an red mistake message

>>> def quest_posit ():
    posit = raw_input("What do you want? ")

    
>>> quest_posit ()
What do you want? an answer

>>> print (posit)
Traceback (most recent call last):
  File "<pyshell#13>", line 1, in <module>
    print (posit)
NameError: name 'posit' is not defined


What can I do ???

help would e really nice

Sorry - why are you using an IDE when clearly you are a complete beginner ? You don't need IDLE (however good it is) or any other IDE to learn python - in fact the above post shows that you are already confused between the IDE and the language.

Ignore the IDE for the moment, just open a terminal and enter : 
```

$ python

```
to start a python interpreter.

Learn to use python using the interpreter, and a simple file editor for longer programs - only then when you are comfortable with the language, and you want to write something more complex, then move to using an IDE.

---

### Post by Dav14 on 2012-06-13
I've Informatiks at school and my teacher started with idle to draw ordinary thiks like a house or a lake. I didn't want to start with something else so I continued with idle. But now I'll try your suggestion : )

---

