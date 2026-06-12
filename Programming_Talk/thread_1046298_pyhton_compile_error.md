---
title: "pyhton compile error"
date: 2009-01-21
forum: Programming Talk
---

### Post by abhilashm86 on 2009-01-21
i just tried simple recursion,created file p4.py

def factorial(n):
if n == 0:
        return 1
else:
        return n * factorial(n-1)

when i imported file p4,following error occured,

>>> import p4
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "p4.py", line 2
    if n == 0:
     ^
IndentationError: expected an indented block

why is this error?

---

### Post by eightmillion on 2009-01-21
You need to indent after a def, like this:

```

def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n-1)
```
Also, if you enclose your code in code blocks, it will make it easier for others to read.

Like this:
[HTML]```
code goes here.
```[/HTML]

---

### Post by abhilashm86 on 2009-01-21
> **eightmillion said:**
> You need to indent after a def, like this:

Like this:
[HTML]```
code goes here.
```[/HTML]
 well i din't quite understand this, but why code is not imported?

---

### Post by lapubell on 2009-01-21
he means that when you put code in your post, surround it with the ```

``` tags so that it shows up nicely.

your code needs to have white space.  it's the way that python knows what is in your function and what isn't.

---

### Post by abhilashm86 on 2009-01-21
oh cool,i'm new to this section,well using namespace means like using it like c++,like
using namespace std

how to just use it in python,give an example as i am new to python.........

---

### Post by Kilon on 2009-01-21
> **abhilashm86 said:**
> well i din't quite understand this, but why code is not imported?


There is a way to import your code , either as an attachment. 

Or as suggested you can wrap the text of your code with [HTML]```
 
```
[/HTML]
or you can press the "#" button in the toolbar.

Also I always advice the use of an IDE it make coding alot easier. 

I use PyDev with Eclipse. It works like a charm for both Python and Jython. Try it , you will love it. You will not need to worry for many things including indentation.

---

### Post by eightmillion on 2009-01-21
> **abhilashm86 said:**
> oh cool,i'm new to this section,well using namespace means like using it like c++,like
using namespace std

how to just use it in python,give an example as i am new to python.........

It's not a namespace problem. Python is very particular about whitespace and indentation.

For example, this code won't work:
```
def factorial(n):
if n == 0:
return 1
else:
return n * factorial(n-1)
```

However, this will:
```
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n-1)
```

---

### Post by abhilashm86 on 2009-01-21
```
def factorial(n):
    if n == 0:
        return 1
    else:
        return n * factorial(n-1)
```[/QUOTE]

yes thanks one again,so indent is important in python even if our code part is correct!!!!i din't know initailly nor my reference book told

well which is better way of doing python,with eclipse or normal way??

---

### Post by eightmillion on 2009-01-21
> **abhilashm86 said:**
> 
yes thanks one again,so indent is important in python even if our code part is correct!!!!i din't know initailly nor my reference book told

well which is better way of doing python,with eclipse or normal way??

Yes, indentation is very important in python. Many other languages use line ending characters and curly braces to separate blocks of code, but python uses whitespace to make the code easier to type and easier to read.

As far as eclipse goes, that's just a matter of personal opinion. I like Stani's Python Editor for writing python.

---

### Post by Kilon on 2009-01-21
If your book does not tell you this basic thing then is time to change book. Until you find a more appropriate book there are excellent tutorial at python's website .

[http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)
[http://python.org/doc/](http://python.org/doc/)

An IDE is always the easiest way to do things. Some call it the lazy way. I call it the efficient way ;) In any case the IDE will do much of the work for you like executing your code , warning as you write for errors  and fixing indentation. Of course you will still need to learn the language . But I find solution like IDE , very helpful especially for finding error as I type them and not after when I execute the programm.

---

