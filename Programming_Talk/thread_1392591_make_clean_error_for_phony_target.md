---
title: "make clean error for phony target"
date: 2010-01-28
forum: Programming Talk
---

### Post by utab on 2010-01-28
Dear all, I have a strange problem with one of my makefiles

The PHONY target clean is defined as

.PHONY : clean
clean:
<tab>rm -rf *.o

right, if I use this way I am getting

makefile:35: *** target file `clean' has both : and :: entries.  Stop.

If I use that as

.PHONY : clean
<tab>rm -rf *.o

That is fine, I could not understand the reason of this difference, even the make manual shows the first usage.

Thanks in advance.
Umut

---

### Post by dwhitney67 on 2010-01-28
What you described for your first attempt should have been fine; is there perhaps something else that you have left out of the discussion.

Give this trivial Makefile a shot:
```

VALUE = 10

.PHONY: clean

clean:
        @echo VALUE = $(VALUE)

```
Note that there is a tab-space before the @echo statement.

P.S.  Avoid using *.o when removing objects files; surely you have an alias called OBJS or something similar.  Use the alias instead:
```

SRCS = $(wildcard *.cpp)
OBJS = $(SRCS:.cpp=.o)
...
clean:
        $(RM) $(OBJS)

```
All it takes is one typo for you to possibly delete all the files in the working folder when using wildcards in a remove (rm) statement.

---

