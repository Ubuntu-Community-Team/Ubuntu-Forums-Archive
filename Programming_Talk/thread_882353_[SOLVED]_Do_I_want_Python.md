---
title: "[SOLVED] Do I want Python?"
date: 2008-08-06
forum: Programming Talk
---

### Post by Zeotronic on 2008-08-06
C++/Python?: I intend to start working on a program, specifically a game, which I want to support plugins which can essentially do anything (because I'm not going to even try to anticipate what someone could want add to it, but I want to support them adding anything anyways). My experience with that is non-existent, and the only interaction I know of that is anything like that is Blender and it's python plugins. I doubt I need to say it, but I don't know anything about python, or it's interaction with applications. **Could anyone tell me if python is what I am, in fact, after, and give me some useful informational sites related to (to your best guess) what I want to do?**

---

### Post by LaRoza on 2008-08-06
If you want plugins, Python would be the best I think for that.

Pick a game engine to work with first, and see what your options are.

---

### Post by pmasiar on 2008-08-06
Python is optimized for flexibility, C++ for effective code. So unless you are extremely skilled (and you looks not), Python is better choice.

BTW later you can anytime to convert parts of Python code to C libraries for speed

---

### Post by LaRoza on 2008-08-07
> **pmasiar said:**
> Python is optimized for flexibility, C++ for effective code.

"effective code"?!

---

### Post by Zeotronic on 2008-08-07
> Pick a game engine to work with first, and see what your options are. 
I figure I'm best off if I make my own... my project doesn't particularly resemble any of the open source games out there, and regardless of that I've already made a nice portion of it (mostly the simple stuff... rendering, audio... haven't quite gotten to networking yet). Maybe I *could* take advantage of someone else's engine, but I'm going to keep working on mine regardless.
> So unless you are extremely skilled (and you looks not), Python is better choice.
Are you trying to say that I could, in fact, go about using C++ for the plug-ins instead of python? Or are you instead trying to say I should use Python for the entire project? If it wouldn't be too difficult to use C++ to do the plug-ins (for myself and any potential other parties), I should probably go with that... I already know C++, where-as in contrast, I would have to learn python (though I'm certainly not without my own reasons, besides this, to learn it).

**Where would be good places to learn about python and, probably, this kind of interaction?**

---

### Post by Wybiral on 2008-08-07
Use Python as much as possible, and only C or C++ for the core if it's needed. You never said what kind of game engine though. But yes, as Blender and GIMP have demonstrated, Python is a great language for plugins and the interpreter can easily be embedded into your C and C++ applications (or your C and C++ code can be linked from your Python application).

---

### Post by Zeotronic on 2008-08-07
Yea, I was reading the tutorial on the Python site, it sounds very promising. Can I expect the python site to eventually cover Embedding (I guess the term is) Python into C/C++? Or will it only talk about embedding C/C++ into Python? Because after I know where I can learn that, after however long it takes me to learn Python, it sounds like I'll be set.

---

### Post by nvteighen on 2008-08-07
> **Zeotronic said:**
> Yea, I was reading the tutorial on the Python site, it sounds very promising. Can I expect the python site to eventually cover Embedding (I guess the term is) Python into C/C++? Or will it only talk about embedding C/C++ into Python? Because after I know where I can learn that, after however long it takes me to learn Python, it sounds like I'll be set.
Not in the Tutorial, but in a different official document:

[http://docs.python.org/ext/embedding.html](http://docs.python.org/ext/embedding.html)

---

### Post by Zeotronic on 2008-08-07
Ok, awesome! Time to learn python!

---

### Post by pmasiar on 2008-08-07
> **Zeotronic said:**
> I figure I'm best off if I make my own... 

If you are kind of person who asks question you did (== not expert with 20 years under belt), your custom engine will be much worse than any existing one. Sorry to break you bad news, but if you never participated in a big project, you don't know yet how much of big picture you are missing.

> Are you trying to say that I could, in fact, go about using C++ for the plug-ins instead of python? 

No.

> Or are you instead trying to say I should use Python for the entire project? 

Not necessarily. Do it all in Python first, measure the bottleneck in need of speedup, try speedup by redesigning in Python, and as last resort - use C. Never once I suggested C++.

> If it wouldn't be too difficult to use C++ to do the plug-ins 

it would. C++ is statically typed. Proper inheritance is paramount and PITA.

> I would have to learn python 

For any decent programmer, learnig Python is weekend project.

> **Where would be good places to learn about python and, probably, this kind of interaction?**[/QUOTE]

start with my sig :-)

---

