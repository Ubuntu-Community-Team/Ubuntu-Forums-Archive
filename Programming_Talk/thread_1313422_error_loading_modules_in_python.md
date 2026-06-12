---
title: "error loading modules in python"
date: 2009-11-03
forum: Programming Talk
---

### Post by Grant A. on 2009-11-03
Hi guys, I made some modules to be loaded into a program that I made. One of them is named monster.py. Well, when I try to do this:

```

import monster
monster.snake()

```

I get this error:

> 
Traceback (most recent call last):
  File "<pyshell#4>", line 1, in <module>
    monster.snake()
AttributeError: 'module' object has no attribute 'snake'


However, when I try it with a similarly named file, monster2

```

import monster2
monster2.snake()

```

I get this output:

> 
snake variables initialized


monster & monster2's contents:

```

def snake():
   print "snake variables initialized"

```

Does anyone know what's going on here?

---

### Post by Can+~ on 2009-11-03
Are you naming your current file (which is importing monster), also monster.py?

---

### Post by Grant A. on 2009-11-03
> **Can+~ said:**
> Are you naming your current file (which is importing monster), also monster.py?

No, the current file is named something else.

---

### Post by Can+~ on 2009-11-03
> **jenniferzhu85 said:**
> [http://www.tradeshoes9.com/](http://www.tradeshoes9.com/)

Spambot reported.

> No, the current file is named something else.

I can't reproduce the error.

Edit:

> Traceback (most recent call last):
File "<pyshell#4>", line 1, in <module>
monster.snake()
AttributeError: 'module' object has no attribute 'snake'

Are you running this on an interactive session? I think that you modified the file, while on an interactive session, and it failed to recompile the file.

---

### Post by Grant A. on 2009-11-03
> **Can+~ said:**
> Spambot reported.



I can't reproduce the error.

Odd, now that I've retried it, I can't either.

What do you think was going on? Glitch in python? Trojan?


Note: I have closed and re-opened the IDLE window since the errors.

---

### Post by Can+~ on 2009-11-03
I modified the file, and got the same error as you, then I did (Python3):

[PHP]>>> import monster
>>> monster.snake()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'module' object has no attribute 'snake'
>>> import imp
>>> imp.reload(monster)
<module 'monster' from 'monster.py'>
>>> monster.snake()
I'm snake, in monster folder[/PHP]

To force recompilation.

---

