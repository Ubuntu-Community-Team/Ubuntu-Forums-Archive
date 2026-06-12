---
title: "Where's my fault? /in python/"
date: 2007-12-25
forum: Programming Talk
---

### Post by cursebg on 2007-12-25
So I'm following this tutorial: [http://www.python.org/doc/tut/tut.html](http://www.python.org/doc/tut/tut.html)
and I'm right here: [http://www.python.org/doc/tut/node6.html#SECTION006710000000000000000](http://www.python.org/doc/tut/node6.html#SECTION006710000000000000000)

When I type a similar stuff:
```
>>> def ask_quit(prompt, opiti=4, complaint='Izhod?'):
...     while True:
...     quit = raw_input(prompt)
  File "<stdin>", line 3
    quit = raw_input(prompt)
       ^
IndentationError: expected an indented block
>>> 

```

I get an error :(
Why am I wrong? :confused:

P.S. And what is "indented"? :oops:

---

### Post by LaRoza on 2007-12-25
> **cursebg said:**
> 
```
>>> def ask_quit(prompt, opiti=4, complaint='Izhod?'):
...     while True:
...     quit = raw_input(prompt)
  File "<stdin>", line 3
    quit = raw_input(prompt)
       ^
IndentationError: expected an indented block
>>> 

```


P.S. And what is "indented"? :oops:

Python expects (and requires) blocks to be indented (4 spaces is standard, so you can make tabs four spaces in your preferences.

```

while True:
    quit= raw_input(prompt)

```
That should fix it. After the while statements, you have to indent its contents.

---

### Post by cursebg on 2007-12-25
AH...right :) thanks !

---

