---
title: "python, trouble with modules"
date: 2009-11-27
forum: Programming Talk
---

### Post by TheLions on 2009-11-27
I wrote one python program which consists of 10 functions. All functions and "main" function are in single file. I would like to chop that single file in several files, that each funtion is in separate file.

e.g.

[COLOR="Red"]#file.py - current state of my prog[/COLOR]
[COLOR="Blue"]def[/COLOR] f1():
[INDENT]bla..[/INDENT]
[INDENT][COLOR="SandyBrown"]return[/COLOR] something[/INDENT]

[COLOR="Blue"]def[/COLOR] f2():
[INDENT]bla..[/INDENT]
[INDENT][COLOR="SandyBrown"]return[/COLOR] something[/INDENT]

[COLOR="Blue"]def[/COLOR] f3():
[INDENT]bla..[/INDENT]
[INDENT][COLOR="SandyBrown"]return[/COLOR] something[/INDENT]

a=f1()
b=f2()
c=f3()
[COLOR="Red"]#end of file.py[/COLOR]

i would like to split it like this:

[COLOR="Red"]#f1.py[/COLOR]
[COLOR="Blue"]def[/COLOR] f1():
[INDENT]bla..[/INDENT]
[INDENT][COLOR="SandyBrown"]return[/COLOR] something[/INDENT]
[COLOR="Red"]#end f1.py[/COLOR]

[COLOR="Red"]#f2.py[/COLOR]
[COLOR="Blue"]def[/COLOR] f2():
[INDENT]bla..[/INDENT]
[INDENT][COLOR="SandyBrown"]return[/COLOR] something[/INDENT]
[COLOR="Red"]#end f2.py
[/COLOR]
[COLOR="Red"]#f3.py[/COLOR]
[COLOR="Blue"]def[/COLOR] f3():
[INDENT]bla..[/INDENT]
[INDENT][COLOR="SandyBrown"]return[/COLOR] something[/INDENT]
[COLOR="Red"]#end f3.py[/COLOR]

[COLOR="Red"]#main.py[/COLOR]
"""import f1, f2, f3"""

a=f1()
b=f2()
c=f3()
[COLOR="Red"]#end of main.py[/COLOR]

How to import f1, f2 and f3 into "main.py" and how to call functions f1, f2 and f3 in "main.py"?

---

### Post by -grubby on 2009-11-27
[http://docs.python.org/tutorial/modules.html](http://docs.python.org/tutorial/modules.html)

---

### Post by TheLions on 2009-11-27
> **-grubby said:**
> [http://docs.python.org/tutorial/modules.html](http://docs.python.org/tutorial/modules.html)

thanks, I dont know how I missed [COLOR="SandyBrown"]from[/COLOR] X [COLOR="SandyBrown"]import[/COLOR] Y in tutorial...

---

