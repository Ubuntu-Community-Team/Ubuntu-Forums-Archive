---
title: "[makefiles] How to edit commands / use conditional statements"
date: 2009-10-22
forum: Programming Talk
---

### Post by AncientPC on 2009-10-22
I want to run different compiler flags depending on which system I'm on (e.g. school machines or laptop).

However I can't get it to run correctly.

```

ifeq (`hostname`,machine.school.edu)
    CC:= -I /lusr/opt/boost1_38/
else
    CC:= -std=gnu++0x
endif

```

The conditional statement never evaluates true for some reason.

---

### Post by Arndt on 2009-10-22
> **AncientPC said:**
> I want to run different compiler flags depending on which system I'm on (e.g. school machines or laptop).

However I can't get it to run correctly.

```

ifeq (`hostname`,machine.school.edu)
    CC:= -I /lusr/opt/boost1_38/
else
    CC:= -std=gnu++0x
endif

```

The conditional statement never evaluates true for some reason.

I think the problem is that the backquote construction doesn't belong to 'make', so it will be comparing the strings "`hostname`" and "machine.school.edu", which are not equal. Backquotes work in commands, because then they are passed to the shell. You can do

```
ifeq ($(shell hostname),machine.school.edu)
    CC:= -I /lusr/opt/boost1_38/
else
    CC:= -std=gnu++0x
endif
```

---

### Post by AncientPC on 2009-10-22
> **Arndt said:**
> I think the problem is that the backquote construction doesn't belong to 'make', so it will be comparing the strings "`hostname`" and "machine.school.edu", which are not equal. Backquotes work in commands, because then they are passed to the shell. You can do

```
ifeq ($(shell hostname),machine.school.edu)
    CC:= -I /lusr/opt/boost1_38/
else
    CC:= -std=gnu++0x
endif
```
That works perfectly, thanks!

---

