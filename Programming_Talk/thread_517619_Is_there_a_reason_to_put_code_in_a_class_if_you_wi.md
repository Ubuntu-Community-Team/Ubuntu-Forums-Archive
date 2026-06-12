---
title: "Is there a reason to put code in a class if you will only have one instance of class?"
date: 2007-08-04
forum: Programming Talk
---

### Post by tc101 on 2007-08-04
In python, is there a reason to put code in a class if you will only have one instance of the class?

---

### Post by Tuna-Fish on 2007-08-04
Yes, to clean it up and make it easier to read, but only if there's a lot of it. You should always write your code to be read, and defining classes to round up similar bits of code together is one good method to do it. However, even here you can of course go too far: If the code is simple and easy to understand, adding a class just complicates things. You absolutely should not adopt a practice of always putting everything in a class just for the heck of it: Adding extra code that serves no practical purpose only makes you do more work, (laziness is a virtue), and risks introducing bugs.

---

### Post by pmasiar on 2007-08-04
If you don't need class behaviour, simpler way might be to have just a module. **but** sometimes having object instance, and not need to pass reference every time, can make code cleaner.

Python is object-**oriented** not object-**obsessed** :-)

---

### Post by kpatz on 2007-08-05
> **pmasiar said:**
> Python is object-**oriented** not object-**obsessed** :-)I like that one. :)

I don't know Python, but I tend to only use classes when I need to take advantage of the encapsulation of them or to create instances of them.  In C++ (for example) there's no point in using a class if you aren't taking advantage of their capabilities.

Java, on the other hand... I guess that's what pmasiar is referring to as "object-obsessed" ;)

---

### Post by scooper on 2007-08-05
Prematurely factoring into classes will make it more difficult to refactor later when you discover more about the problem and the solution (inevitable).  I even get rid of classes when I discover they don't provide any benefit by being a class.  I also don't add methods to data objects unless it's absolutely obvious it belongs there, and it cleans up a lot of calling code.

I've found excessively objectified programs to be some of the hardest to figure out and maintain.  I went through the "objects are wonderful" stage with C++ and Java, and got over it (with Python).

---

### Post by the_unforgiven on 2007-08-05
> **tc101 said:**
> In python, is there a reason to put code in a class if you will only have one instance of the class?
Yes, at times, you need to do precisely that - and it's a very well defined design pattern called **Singleton**:
[http://en.wikipedia.org/wiki/Singleton_pattern](http://en.wikipedia.org/wiki/Singleton_pattern)

However, this is not specific to object-oriented programming.
Singleton objects exist in procedural languages too.

HTH ;)

---

### Post by pmasiar on 2007-08-05
One reason why ie Java forces object on you is when you need to return a value which is not simple scalar (value or reference), but something more complicated. But in Python, is easy to return a tuple and unpack it on asignment, or to whip a dictionary.

```

def t():
    return 1,"hi" # return a tuple instead of full-blown object

x, y = t() # unpack tuple

```

---

