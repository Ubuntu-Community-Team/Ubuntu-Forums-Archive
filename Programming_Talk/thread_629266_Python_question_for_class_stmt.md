---
title: "Python: question for class stmt"
date: 2007-12-02
forum: Programming Talk
---

### Post by vmsda on 2007-12-02
Following a python tutorial I am using, I invoke python from a terminal, get the prompt and type:

>>> import math
>>> class Point:
...         p = Point()
...         p.x = 3.0
...         p.y = 4.0
...    distance = math.sqrt(p.x**2 + p.y**2)
        File "<stdin>", line 5
       distance = math.sqrt(p.x**2 + p.y**2)
                  ^

Syntax error: invalid syntax
>>>

Why do I get this error? All the examples from the same tutorial have thus far worked, but not this one. Any hints, please?

---

### Post by NovaAesa on 2007-12-02
Is there anymore code before that you are executing?

I'm getting this when I type what you have into the interpreter, which is a completely different error.
[PHP]
>>> import math
>>> class Point:
...     p = Point()
...     p.x = 3.0
...     p.y = 4.0
...     distance = math.sqrt(p.x**2 + p.y**2)
... 
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 2, in Point
NameError: name 'Point' is not defined
[/PHP]

---

### Post by smartbei on 2007-12-02
It does not make sense to have 'class Point:', since you are not defining a class - you are using it.
Try this:
```

import math
class Point:
	def __init__(self):
		self.x = 0
		self.y = 0

p = Point()
p.x = 3.0
p.y = 4.0
distance = math.sqrt(p.x**2 + p.y**2)

```
Here, I define the class Point and create its attributes x and y.

@vmsda: Your specific error may be cause by too much/lack of whitespace, which I can't tell since you didn't post the code in [ code ] blocks (please do so in the future :D).

Also, if you are having problems with a specific tutorial why didn't you link it? That would have helped me in getting a full picture of where your problem may lie.

---

### Post by vmsda on 2007-12-02
Thank you for your append, NovaAsea.

The difference is that you indented the "distance = math ...." instructions, whereas I did not indent it when I executed.

---

### Post by vmsda on 2007-12-02
Thank you for your help, smartbei.

I reproduced your code in my system and it worked.

One can find the tutorial at [http://www.greenteapress.com/thinkpython](http://www.greenteapress.com/thinkpython), and I took the example I reproduced from chapter 15. This class definition/usage syntax is very obscure; in trying to find out what was happening I read a bit of the official Python Tutorial in the documentation and came out of it, if anything, even more confused!

I have no idea on how to reproduce code in the format you did. Can you give me a pointer to instructions on how to go about it?

---

### Post by tyoc on 2007-12-02
Havent seen that reference, I will check it (thought the original book yes). (Now that I remember I have seen it 1 time)


>  I have no idea on how to reproduce code in the format you did. Can you give me a pointer to instructions on how to go about it?What you mean? you dont know how to TAB?, in your editor search in options and put TAB indents with spaces, and put 4 spaces.

> This class definition/usage syntax is very obscure; [http://docs.python.org/tut/node11.html](http://docs.python.org/tut/node11.html)

If you are referring to "obscure" because you see definition of the so called "methods", the first argument is "self" do the following in console

> import thisYou will see that explicit is best than implicit, java, C++, and other langs hide the fact that a pointer/reference to the object that call is passed to the function (see the semantic difference of call it a "method") like the first argument, that is why in C++ you do this->member.


If you are refering to how is that self.memmber1 = True or x = True is a member, read this: [http://docs.python.org/tut/node11.html#SECTION0011320000000000000000](http://docs.python.org/tut/node11.html#SECTION0011320000000000000000)

>  Class objects support two kinds of operations: attribute references and instantiation.

---

### Post by smartbei on 2007-12-02
I think he meant how to get the code to look right in the forum. Assuming that is indeed the case: Put **[ code ]** (without the spaces) before your code and **[ /code ]** (without the spaces) after your code.

---

### Post by pmasiar on 2007-12-02
In Python, you do not **have to** define objects untill you are ready. So for beginners, i would recommend firt to write plain non-OOP procedural code, using OO libraries when available, but not bothering by OO design first.

Later, after couple months, when you are more familiar with error messages, syntax, and debugging, you can look at OOP. Python is not OOP-obsessed like java is, many people can squeak by using procedural code and existing OO libraries.

---

### Post by vmsda on 2007-12-03
Thank you for your kind advice, pmasiar - certainly more constructive than the arrogance implicit in the "import this" attitude of a previous append. I shall follow one of your leads and see how I fare.

---

