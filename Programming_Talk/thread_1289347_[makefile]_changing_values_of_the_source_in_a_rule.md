---
title: "[makefile] changing values of the source in a rule"
date: 2009-10-12
forum: Programming Talk
---

### Post by mangar on 2009-10-12
Hi all,
I'm trying to do the following:
When using one of the following rules:

$(C_OBJECTS): %.o: $(addprefix $(dir %.c)../, $(notdir %.c) )

or 

$(C_OBJECTS): %.o : $(subst /Obj/,/,%.c)

I get an error that the a.c needed by a.o isn't found

What need I do in order to get a working rule?

---

