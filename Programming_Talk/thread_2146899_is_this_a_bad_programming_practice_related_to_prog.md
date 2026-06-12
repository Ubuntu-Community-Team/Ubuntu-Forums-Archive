---
title: "is this a bad programming practice related to program architecture ?"
date: 2013-05-20
forum: Programming Talk
---

### Post by IAMTubby on 2013-05-20
Hello,
I observed this kind of architecture in a project I'm working on.

**Scenario**
Assume sourcefile1.c calls a function defined in sourcefile2.c,

**What I would do to build the project is:**
gcc -o finalexe sourcefile1.c sourcefile2.c

**What I observe in the project is:**
Within sourcefile1.c, they do a #include "sourcefile2.c"

**Problem**
This makes it difficult for me to understand code flow(while working on a bigger project), because by looking at the makefile, I can't figure out how the files are linked. I would kinda have to go inside each file to see the #include's and understand how they are linked to each other.

No worries, I have got it using some grep'ping skills, but just want to know if this is bad architecture.

Please advise.
Thanks.

---

### Post by ehrt74 on 2013-05-20
Usually you use header files ( myfunctionaliy.h ) to declare things which are implemented in the source files ( myfunctionality.c ). This makes scanning the code quickly a lot easier.

Apart from that I can only really recommend that you choose your names very carefully.

---

### Post by trent.josephsen on 2013-05-20
Yes, it is bad architecture, but maybe not for the reason you're thinking.

For starters, it makes sourcefile1.c depend on sourcefile2.c: they can't be compiled independently. For two files this might not make much difference, but for large projects you don't want to have to re-compile the whole directory structure just because you made one change. Furthermore, it means if you use any of the functions in sourcefile2.c from any other file, you have to recompile it in its entirety as many times as it is #included.

In a well-designed project, the .c files don't "depend" on each other; they can be compiled independently into .o files which can then be linked together to create an executable file. Whether fileA calls functions defined in fileB or the other way around (or both) is irrelevant. What's more, you can create a drop-in replacement for fileB (fileB_r2.c), compile it by itself, and link it instead of the original fileB without changing anything but the makefile. That is, assuming you have a fileB.h header file and use it correctly.

---

### Post by IAMTubby on 2013-05-20
> **trent.josephsen said:**
> Yes, it is bad architecture, but maybe not for the reason you're thinking.

Thanks a lot trent, that was very insightful. That clears my question.

Thanks ehrt74.

---

