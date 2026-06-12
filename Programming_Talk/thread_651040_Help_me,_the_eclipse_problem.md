---
title: "Help me, the eclipse problem"
date: 2007-12-27
forum: Programming Talk
---

### Post by nethibernate on 2007-12-27
Hi, All!
i got eclipse crash when i was running it. The error message is :

java.lang.OutOfMemoryError: PermGen space
Exception in thread "main" java.lang.OutOfMemoryError: PermGen space

Help me! What should i do? Now i can't use it normally!:confused::confused:

---

### Post by bmbernie on 2007-12-27
Does this happen every time you start eclipse? 
How much free memory do you have?

---

### Post by nethibernate on 2007-12-27
I got 1G memory and i'm sure there was enough memory when the error occurs.

---

### Post by jespdj on 2007-12-28
Read the README that comes with Eclipse. This is a problem in Eclipse 3.2 (solved in Eclipse 3.3).

You need to start Eclipse with extra memory parameters. See [this](http://tassos.blogentis.net/2006/06/08/eclipse-and-permgen-space), for example.

Use Google to search for "eclipse permgen".

---

