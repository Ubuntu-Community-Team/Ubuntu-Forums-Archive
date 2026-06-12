---
title: "gtk+ installation wont work"
date: 2007-10-27
forum: Programming Talk
---

### Post by drosophyllum on 2007-10-27
Im learning gui programming and well im starting with gtk. Only problem is ive tried to install it using ubuntu's package for it and it still wont work. I put the header in my program and it wont compile with the error that gtk wasn't found. 

Im a noob with gui  and programing so exuse my ignorance.

---

### Post by johnnyg on 2007-10-27
To do gtk development in C/C++ you will need the development packages installed.

sudo aptitude install libgtk2.0-dev

will probably do the trick for you.

More generally, when stuff like this is missing, look for a -dev package, that is usually what is needed.

If you are really new to programming and GUI's I'd recommend learning python:

[http://www.python.org](http://www.python.org)

You could then do gui coding in python using gtk, just make sure you have this package:

python-gtk2

John

---

### Post by drosophyllum on 2007-10-27
so when i program what should i put as the header file. I had that install my problem is i cant get it to work or get to use it.

what is wrong with this:

#include<gtk>

when i use this include statment, the compiler says there is no such thing, even after ive installed the library.

---

