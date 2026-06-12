---
title: "Overused OOP and patterns"
date: 2009-02-17
forum: Programming Talk
---

### Post by spupy on 2009-02-17
Recently I started learning Python. Now I've decided to explore the OOP side of python, and I'm really stumped. Maybe I'm thinking in java (damn you, Bruce Eckel! :)). PLEASE NOTE, this isn't a java-vs-python discussion, but a talk about some things that the different ideas of python brought to my attention. Two examples:
1. Static variables (a.k.a global variables). At first I didn't find a simple way to declase static variables and methods in python. I googled a bit and people say that global variables aren't great, and that programmers shouldn't use them that much. 
2. The Singleton-Pattern. Or is it an antipattern?
Python made me realize that some techniques I've been using for so long may not always be the best solution for a problem.
[B]
TL;DR : Discuss OOP ideas and design patterns that are frequently used, but shouldn't be.[/B]

---

### Post by Can+~ on 2009-02-17
> **spupy said:**
> 1. Static variables (a.k.a global variables). At first I didn't find a simple way to declase static variables and methods in python. I googled a bit and people say that global variables aren't great, and that programmers shouldn't use them that much. 


Global variables are never a good idea, only on small snippets of code. Why? Because you start losing control of data, by leaving a variable open for being written over it. Later, when your program gets bigger, functions that depend on said global will start getting random results, as another function may be messing with the contained value.

In other words, it's a long-term pain in the butt.

---

### Post by CptPicard on 2009-02-17
> **spupy said:**
> 
1. Static variables (a.k.a global variables). At first I didn't find a simple way to declase static variables and methods in python. I googled a bit and people say that global variables aren't great, and that programmers shouldn't use them that much. 
2. The Singleton-Pattern. Or is it an antipattern?

First of all, there are "class" (static) variables... they exist in Python all right.

For globals, the concept you're looking for is modules. They are essentially namespaces -- hashes from names to objects, just like Python's objects themselves are. If you define X = 1 in some module (file), you can import that X from other modules.


> 
Python made me realize that some techniques I've been using for so long may not always be the best solution for a problem.

You got that right. A lot of OOP patterns are ways to express stuff in a situation where you explicitly have to define a type for everything, and where encapsulation is a problem to get around through design. Read 

[http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html](http://steve-yegge.blogspot.com/2006/03/execution-in-kingdom-of-nouns.html)

---

### Post by era86 on 2009-02-17
> **Can+~ said:**
> Global variables are never a good idea, only on small snippets of code. Why? Because you start losing control of data, by leaving a variable open for being written over it. Later, when your program gets bigger, functions that depend on said global will start getting random results, as another function may be messing with the contained value.

In other words, it's a long-term pain in the butt.

Original poster mentioned "static" global variables.  These cannot be modified, so there would be no issue with that.  I think, if used wisely, global variables can be quite handy especially with programming systems and such.  BUT, they must be used carefully because issues such as the one mentioned by Can+~ will arise.

---

### Post by spupy on 2009-02-17
> **era86 said:**
> Original poster mentioned "static" global variables.  These cannot be modified, so there would be no issue with that.  I think, if used wisely, global variables can be quite handy especially with programming systems and such.  BUT, they must be used carefully because issues such as the one mentioned by Can+~ will arise.

I meant global variables, sorry. This is not really about how they are implemented in Python, either, rather, should I use them.

What about class/static variables then?

---

### Post by jimi_hendrix on 2009-02-17
> **era86 said:**
> Original poster mentioned "static" global variables.  These cannot be modified, so there would be no issue with that.  I think, if used wisely, global variables can be quite handy especially with programming systems and such.  BUT, they must be used carefully because issues such as the one mentioned by Can+~ will arise.

globals are like goto :)

can either save you a lot of trouble or be a pain

---

### Post by CptPicard on 2009-02-17
> 
What about class/static variables then?

Well, that is a design decision of course. Nothing wrong with a class variable if it is obviously something that belongs to that entire class of objects.

Interestingly, in Python class (and even object member!) and global (module-namespace) variables behave very similarly because everything really is just a namespace-hash-object. Even globals aren't such a bad thing if you isolate them into the module where they exist, and preferably just alter them from inside code in that same module (while taking care of threading issues of course). In procedural-style python, this is how you'll do things anyway -- the modules are kind of global singleton objects in themselves, if you will.

---

### Post by nvteighen on 2009-02-17
> **CptPicard said:**
> Well, that is a design decision of course. Nothing wrong with a class variable if it is obviously something that belongs to that entire class of objects.

Interestingly, in Python class (and even object member!) and global (module-namespace) variables behave very similarly because everything really is just a namespace-hash-object. Even globals aren't such a bad thing if you isolate them into the module where they exist, and preferably just alter them from inside code in that same module (while taking care of threading issues of course). In procedural-style python, this is how you'll do things anyway -- the modules are kind of global singleton objects in themselves, if you will.
Which is one if my major dislikes of Python in favor of the Perl approach, where you define when to create a new namespace and when not (the **package** statement). I know Python is not OOP-obsessed as Java, where a single "Hello World" makes explicit use of classes. But in Python you have OOP behaivor everywhere and that is, IMO, sometimes a bit annoying.

Why? Because it finally forces you to OOP sooner or later. Think of any simple interaction you do with a list and there you have methods and attributes. I know OOP is kind more intuitive for beginners than bare ol' style procedural programming, but it also drives to a monoparadigm learning that is a bit difficult to override later. OOP is really useful, but sometimes it's more an obstacle than a help (well, sometimes you just don't have an "object class" to think of... just a procedure).

---

### Post by PythonPower on 2009-02-17
[QUOTE=nvteighen]Why? Because it finally forces you to OOP sooner or later. Think of any simple interaction you do with a list and there you have methods and attributes. I know OOP is kind more intuitive for beginners than bare ol' style procedural programming, but it also drives to a monoparadigm learning that is a bit difficult to override later. OOP is really useful, but sometimes it's more an obstacle than a help (well, sometimes you just don't have an "object class" to think of... just a procedure).[/QUOTE]

There are some exceptions too. len(arr) for array length as well as arr.__len__(); the len() function just delegates to the magical object-orientated method.

---

### Post by Wybiral on 2009-02-17
> **PythonPower said:**
> There are some exceptions too. len(arr) for array length as well as arr.__len__(); the len() function just delegates to the magical object-orientated method.

For dynamic languages like Python, I really like this pattern. It encourages the construction of uniform interfaces, but not in the strict OO kind of way (where everything has to be explicitly defined as such). If you follow the idiom, you no longer have to remember what attribute or method it is to get the length of some arbitrary data structure, there is an implied standard interface for these things.

"I don't care if you toss me a real duck or a person that thinks they're a duck, all I care about is that it can quack" And why should I go through all the trouble to implement some kind of type hierarchy just to prove that my thing can quack for you? If you squeeze him and he doesn't quack, just yell exceptions at me so I can figure out what went wrong.

The duck-accepting helper functions provide a funnel that encourages uniformity in design. If you implement some kind of 'render(x)' that calls 'x.__render__()' then you're laying out an interface for renderable objects... Anything that wants to be renderable just needs to provide the right method, and there's no need for all the excessive type/interface hierarchy and  baggage that you would get with more strict OO languages.

Not to mention the minor perk of being able to say map(len, objs) or map(str, objs) without having to provide some kind of lambda/method-caller to do so (such as map(lambda x: x.str(), objs) or something)

---

### Post by Can+~ on 2009-02-17
> **Wybiral said:**
> For dynamic languages like Python, I really like this pattern. It encourages the construction of uniform interfaces, but not in the strict OO kind of way (where everything has to be explicitly defined as such). If you follow the idiom, you no longer have to remember what attribute or method it is to get the length of some arbitrary data structure, there is an implied standard interface for these things.

That's a great point. The main reason I drop a language, is because the developers having their heads so up their ... "behinds", that they can't see that the same rigid environment that once was useful and productive, now is hampering the development by becoming a burden.

---

