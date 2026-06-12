---
title: "Problems with IDLE using python 3.1"
date: 2010-10-16
forum: Programming Talk
---

### Post by poodoopealeoaph on 2010-10-16
I was just having some issues where I am trying to use IDLE with python 3.1 and whenever I try simple commands (because I am a beginner and am reading through appress, great book by the way) it gives me syntax errors. No matter how many different things I try, it will not work. If I open up Konsole though and try the same exact code, it will work. So, am I just missing some package for python? 

by the way the code was just the intro thing:
 ```
>>>print "hello, world!"
```

in Konsole I get:
```
>>>print "hello, world!"
hello, world!
```

in IDLE using python 3.1 I get:
```
>>> print "hello, world"
SyntaxError: invalid syntax
```

---

### Post by The Cog on 2010-10-16
In python 3, print was changed to being a function, so you have to do:
> print("hello, world")
instead.

Moved to Programming Talk forum.

---

### Post by crichard on 2010-10-16
```
print('Hello World')
```

This syntax works in both python & python3.

---

### Post by juancarlospaco on 2010-10-16
You can run 2to3 from terminal to make your python 2.x sintax compatible with python 3.x sintax.

---

