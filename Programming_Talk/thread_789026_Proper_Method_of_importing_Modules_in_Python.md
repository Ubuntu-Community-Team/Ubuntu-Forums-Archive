---
title: "Proper Method of importing Modules in Python?"
date: 2008-05-10
forum: Programming Talk
---

### Post by regomodo on 2008-05-10
`

---

### Post by smartbei on 2008-05-10
In general, use: ```
import [module]
```so as to not clutter up the global namespace. If there is a specific function or two that you use a lot then you can do: ```
from [module] import [func]
```.

Generally stay away from ```
from [module] import *
``` except for modules that are meant for this use - such as Tkinter.

---

### Post by LaRoza on 2008-05-10
There are several ways of importing.

[php]
//imports easygui the most common way
import easygui

//import only system from the os module. 
//You can call "system()" without cluttering the namespace
from os import system

//This is like the first option, but instead of having to write:
//   curses.initscr()
//You use:
//   cs.initscr()
//It saves typing
import curses as cs
[/php]

In general, don't do "import *" for anything. It seems that GUI toolkits like Tkinter and QT make it safer by having everything in the module have a prefix (Tk, Q)

---

### Post by Can+~ on 2008-05-10
You could use import * for modules you have created, but with proper planning before using them. 

In general, stay away from the "*", as everyone has stated, except for particular cases, like OpenGL.

---

### Post by pmasiar on 2008-05-10
Funny you guys (and gals :-) ) explain best practices, but do not explain **why** they are best. It is dangerously close to [http://en.wikipedia.org/wiki/Cargo_cult_programming](http://en.wikipedia.org/wiki/Cargo_cult_programming) :-)

I am not sure that OP is grokking phrase "clutter global namespace" (and yes, if you are wondering, I **finally** get my hands on  "Stranger in a strange land", and it changed my perception of understanding :-) I cannot recommend it high enough. It you did not read it, don't walk: run to library!).

"from module1 import *" will import all names defined in module1, correct. How does it clutter? Because if you do not know what those names are, and by mistake define such name, or import same name from another module: one of the names will be lost, gets overwritten by the other (and if name of the function, the functionality is gone), and confusion is certain: Error messages will be cryptic, you will be lucky if you have wrong number of parameters, or obvious type error. I've seen it happen, and is rather confusing for a beginner (obvious for expert, but experts would not do it :-) )

Why some modules use it, and why it is right for them? Because they define so long and ugly names you would almost never dream to name your own objects that way - and if you do, by accident, you **will** have to face the music. So learn what you are importing, and be careful not to override those names.

As the saying goes, Python does not force anything on you, it assumes programmers are consenting adults. You have power to do whatever you want, but you also have responsibility to deal with consequences of your bad decisions. With great power comes great responsibility, but you already knew that :-)

If 'module1' is too long name to type, "import module1 as m1", or import just couple of names you need: from module1 import name1, name2.

It is always better to ask such question that just do it in some way without understanding why - that way lays cargo cult. Problem is, understanding takes time, cargo cult programming (without real deep grokking) is much simpler and less time consuming.

---

### Post by LaRoza on 2008-05-10
> **pmasiar said:**
> Funny you guys (and gals :-) ) explain best practices, but do not explain **why** they are best. It is dangerously close to [http://en.wikipedia.org/wiki/Cargo_cult_programming](http://en.wikipedia.org/wiki/Cargo_cult_programming) :-)

I am not sure that OP is grokking phrase "clutter global namespace" (and yes, if you are wondering, I **finally** get my hands on  "Stranger in a strange land", and it changed my perception of understanding :-) I cannot recommend it high enough. It you did not read it, don't walk: run to library!).

It is always better to ask such question that just do it in some way without understanding why - that way lays cargo cult. Problem is, understanding takes time, cargo cult programming (without real deep grokking) is much simpler and less time consuming.

You are right, we didn't explain it. D'oh.

Of course, we have to talk about your use of hacker slang on newbs ;) Not all newbs grok [Hacker slang]("http://www.catb.org/~esr/sf-words/glossary.html").

---

### Post by regomodo on 2008-05-11
`

---

