---
title: "Embedding multiple languages into my C program?"
date: 2008-11-10
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-10
As title says, how could I embed Python and C++ in my C program?

---

### Post by WW on 2008-11-10
Start at the source, docs.python.org: [Embedding Python in Another Application](http://docs.python.org/extending/embedding.html)

---

### Post by crazyfuturamanoob on 2008-11-10
Ok. Tried the example from that site just to see if it works:
```
#include <Python.h>

int
main(int argc, char *argv[])
{
  Py_Initialize();
  PyRun_SimpleString("from time import time,ctime\n"
                     "print 'Today is',ctime(time())\n");
  Py_Finalize();
  return 0;
}
```
But it doesn't seem to find/load Python.h. At least it doesn't want to compile because Py_Initialize() and Py_Finalize() aren't declared.

And I have python-dev installed. What could be the problem?

---

### Post by CptPicard on 2008-11-10
By the way, just so you know.. it goes more easily the other way around. You may want to consider writing the high level in Python and calling into C. Also, using C++ from C is nastier than the other way around...

---

### Post by crazyfuturamanoob on 2008-11-10
> **CptPicard said:**
> By the way, just so you know.. it goes more easily the other way around. You may want to consider writing the high level in Python and calling into C. Also, using C++ from C is nastier than the other way around...

But I want use python just as a scripting language for my game.

Here's one error I got:
[HTML]error: Python.h: No such file or directory[/HTML]
Whops html tags too lazy to replace.

---

### Post by geirha on 2008-11-10
Header files are in -dev-packages. So, if you are using python2.5, install [apt://python2.5-dev](apt://python2.5-dev) and find the compilation flags you need to use with 
```
python2.5-config --cflags
```
and linker flags with
```
python2.5-config --ldflags
```

---

### Post by pp. on 2008-11-10
Actually, you can not embed 'languages' in a C program. Also, there's no easy way to embed lines of code of another language in your C program. You can, however, write bits and pieces of your application in other languages, compile those and call the compiled parts from your C program.

This may sound like 'mere' semantics, but I rather believe that you need to sort out the concepts involved in order to make head or tail of any sensible answers you receive in this thread.

---

### Post by achelis on 2008-11-10
> **crazyfuturamanoob said:**
> But I want use python just as a scripting language for my game.

Here's one error I got:
[HTML]error: Python.h: No such file or directory[/HTML]
Whops html tags too lazy to replace.

[http://ubuntuforums.org/showthread.php?t=384729]("http://ubuntuforums.org/showthread.php?t=384729")

and

[http://mail.python.org/pipermail/python-list/2006-August/398824.html]("http://mail.python.org/pipermail/python-list/2006-August/398824.html")

Worked for me :)

---

### Post by crazyfuturamanoob on 2008-11-10
> **achelis said:**
> [http://ubuntuforums.org/showthread.php?t=384729]("http://ubuntuforums.org/showthread.php?t=384729")

and

[http://mail.python.org/pipermail/python-list/2006-August/398824.html]("http://mail.python.org/pipermail/python-list/2006-August/398824.html")

Worked for me :)

Got it working, added the python flags into makefile. :)

---

