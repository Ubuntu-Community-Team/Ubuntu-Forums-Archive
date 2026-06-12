---
title: "[Python] Variable scopes with OOP?"
date: 2008-08-23
forum: Programming Talk
---

### Post by linkmaster03 on 2008-08-23
I'm starting to learn OOP in Python, and I'm confused as to how variable scope works differently using classes. Because I probably have a ton of unneeded function arguments...

---

### Post by WW on 2008-08-23
It would help if you asked a more specific question.  Otherwise, the best anyone can probably do is point you to something like [Chapter 9](http://docs.python.org/tut/node11.html) of the [Python Tutorial](http://docs.python.org/tut/tut.html).

---

### Post by linkmaster03 on 2008-08-23
OK, I declare my variables right after my imports outside of any classes. Then I pass those as an argument to my first function, and if I use any of those variables in other functions or other functions in different classes, I pass them as arguments. When do I need to pass variables as arguments, and when are they global?

---

### Post by days_of_ruin on 2008-08-23
If you declare a variable outside of a function or class
it is global.But passing variables as arguments is less error prone
and easier to understand what is going on.

So just keep doing what you were doing.

---

### Post by pmasiar on 2008-08-23
How much experience you have with Python in simple procedural programming, without defining your own objects? maybe you jumped to OOP too soon? You can happily program in Python without OOP, it's not Java.

Read docs, my explanation is not as well thought as the docs (they had more time), assuming you did read it, here is mine:

Variable scope has nothing to do with OOP. If you have a modul variable outside of function definition, and use it's value, Python uses the "global" value. But if you try to assign to it, you have to define it as global inside function namespace, or Python will try to prevent side-effect (changing a global) and creates local variable of same name for you.

---

### Post by imdano on 2008-08-24
Just to illustrate what pmasiar described:

[php]foo = 2

def bar():
    foo = 6

bar()
print foo[/php]This would print 2

[php]
foo = 2

def bar():
   global foo
   foo = 6

bar()
print foo[/php]This would print 6

---

### Post by pmasiar on 2008-08-24
> **dwhitney67 said:**
> If you are indeed new to Python, perhaps you should consider learning C++ or Java instead.

Why?

After the pain of C++, Python will feel so much easier and simpler? :-)

---

