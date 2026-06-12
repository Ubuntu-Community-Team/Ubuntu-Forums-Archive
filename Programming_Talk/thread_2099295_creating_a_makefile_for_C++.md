---
title: "creating a makefile for C++"
date: 2012-12-29
forum: Programming Talk
---

### Post by micahpage on 2012-12-29
If you have multiple cpp files, h files, or even some in dubdirectories, what do you put in the makefile?

For example,
```
metulburr@ubuntu:~/Documents/cplusplus/composition$ ls
Birthday.cpp  Birthday.h  main.cpp  People.cpp  People.h
metulburr@ubuntu:~/Documents/cplusplus/composition$ 
```

---

### Post by dwhitney67 on 2012-12-29
Start by reading/researching:  [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)


For the simple project layout you posted, the following basic/simple Makefile should suffice:
```

# Application name; change if needed.
APP = bday

# Listing of source code files
SRCS = Birthday.cpp main.cpp  People.cpp

# Formulate the names of the respective object files
OBJS = $(SRCS:.cpp=.o)

# Define appropriate compiler options
CXXFLAGS = -Wall -pedantic

# Define appropriate link options and libraries
LDFLAGS =
LIBS =


.PHONY = all clean


all : $(APP)


$(APP) : $(OBJS)
        $(CXX) $^ $(LDFLAGS) $(LIBS) -o $@


clean :
        $(RM) $(OBJS) $(APP)

```


Note:
```

$(APP) : $(OBJS)
<tab-space>$(CXX) $^ $(LDFLAGS) $(LIBS) -o $@


clean :
<tab-space>$(RM) $(OBJS) $(APP)

```

---

### Post by bird1500 on 2012-12-30
It's slightly off topic, but if you haven't  considered cmake yet, imo you should. If you go the make route you'll have to learn/use autotools, also known as autohell, cmake is much simpler (and crossplatform), more modern and faster. (And yes, nothing is ideal, but some things are generally (much) better than others).

---

### Post by dwhitney67 on 2012-12-30
> **bird1500 said:**
> ... If you go the make route you'll have to learn/use autotools...
Your assumption is incorrect.  I use Makefiles all the time; never once have I had to use autotools.

---

### Post by bird1500 on 2012-12-30
> **dwhitney67 said:**
> Your assumption is incorrect.  I use Makefiles all the time; never once have I had to use autotools.
Please check my spelling too. When people say something they don't mean it in absolute terms, unless explicitly told so.

---

