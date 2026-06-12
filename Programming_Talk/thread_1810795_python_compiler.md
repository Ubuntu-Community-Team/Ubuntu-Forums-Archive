---
title: "python compiler"
date: 2011-07-23
forum: Programming Talk
---

### Post by rpmp on 2011-07-23
how do u compile programs in python using ubuntu?

---

### Post by CptPicard on 2011-07-23
Any particular reason why you'd want to do this?

---

### Post by rpmp on 2011-07-23
im not even sure if u can compile python programs on linux im asking if u can and with wath?

---

### Post by CptPicard on 2011-07-23
Well, there is something like psyco, but mostly you just run it through the regular interpreter...

---

### Post by Thewhistlingwind on 2011-07-23
I think he means to bytecode.

Anyway, I'm pretty sure you want the py compile module.

[http://effbot.org/zone/python-compile.htm](http://effbot.org/zone/python-compile.htm)

Have fun!

---

### Post by TwoEars on 2011-07-23
> **rpmp said:**
> how do u compile programs in python using ubuntu?

Depends entirely on what you mean and what you understand. Clarify that, and you'll get your answer ;)

---

### Post by Lux Perpetua on 2011-07-23
> **rpmp said:**
> how do u compile programs in python using ubuntu?Simple: you don't. You run them with the python interpreter: ```
$ python my_program.py
``` (9:1 odds the OP just doesn't know that there are such things as "compiled" and "interpreted" languages.)

---

### Post by Dhiraj Thakur(Invincible) on 2011-07-24
> **Lux Perpetua said:**
> Simple: you don't. You run them with the python interpreter: ```
$ python my_program.py
``` (9:1 odds the OP just doesn't know that there are such things as "compiled" and "interpreted" languages.)
The answer Lua gave is correct.....if you want a standalone executable you should consider pyinstaller or py2exe....

---

### Post by The Cyph3r on 2011-07-24
Try C++ if you want to compile.

---

### Post by nvteighen on 2011-07-24
At least on Debian, PyCentral installs a command called py_compilefiles, which is used for deb packaging using PyCentral. I'm not sure if it's even called by default when building the deb package.

But really, why do you want to do this? It's highly impractical during development and it brings little advantages. Disassembling a Python module is extremely easy... (all you need is a core module, not any arcane tool!).

---

### Post by StephenF on 2011-07-24
> **Dhiraj Thakur(Invincible) said:**
> The answer Lua gave is correct.....if you want a standalone executable you should consider pyinstaller or py2exe....
And with Ubuntu there is nothing to be gained from a standalone executable.

To compile to bytecode just import your program.
```

$ python
Python 2.7.1 (r271:86832, Apr 18 2011, 19:52:46) 
[GCC 4.4.5] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import myprogram

```
This generates myprogram.pyc, but really there is no need for such things until you are using some kind of build system for your project. It saves a few milliseconds, that's all.

---

