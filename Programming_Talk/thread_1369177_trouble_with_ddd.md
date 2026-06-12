---
title: "trouble with ddd"
date: 2009-12-31
forum: Programming Talk
---

### Post by swappo1 on 2009-12-31
Hello,

I am trying to debug a program with ddd.  When I try and load the program from the command line ($ddd Pong &) I get an error when ddd opens.  I run make beforehand so the program is comiled.  The error is: /home/.../init.c   No such file or directory.  However, there is no init.c in my directory.  I don't seem to be having a problem when I use gdb so it seems to be something with ddd.  Also, I tested ddd out using another program from the following site: [http://www.ibm.com/developerworks/library/l-gdb/](http://www.ibm.com/developerworks/library/l-gdb/) while using the same exact makefile, and ddd loads this fine.  Any ideas how to get ddd to open the file?

---

### Post by swappo1 on 2009-12-31
I was wrong, It won't work with gdb either.  I use the SDL library in my program.  Could this have anything to do with it?

---

### Post by dwhitney67 on 2010-01-01
Does your project have an 'init.c' file?

Did you compile your source files with the '-g' option?

Did you Google for "ddd init.c"?  You may have found a link such as this [one]("http://www.linuxquestions.org/questions/programming-9/ddd-doesnt-work-226540/"), which indicated that the '-g' option is indeed needed.  Or maybe this [link]("http://expert.mandriva.com/question/49156").  As you can see, the question has been asked and answered ad-nauseum.  Hopefully the solution will work for you too.

---

### Post by swappo1 on 2010-01-01
I think I figured it out.  I wasn't exactly sure where to put -g in Makefile.  The place I had it allowed some programs to load and be debugged in ddd but not others.  I moved -g and was able to get it to work in ddd.  Hopefully this is the right place.
```
CXXFLAGS = -g -O2 -Wall -Werror -ansi
LDLIBS = -lSDL_image -lpthread
INCLUDE = .
PROG = pong
NAME = pong
SRCS = main.cpp GameLoop.cpp Display.cpp Ball.cpp
OBJS = main.o GameLoop.o Display.o Ball.o

$(PROG): $(OBJS)
		$(CXX) -o $(PROG) $(OBJS) $(LDLIBS)
		#mv $(PROG) ..

# How to make the object files:

-include deps.mak

deps:
		$(CXX) -MM $(SRCS) > deps.mak

# Cleaning target (only works with fileutils):

clean:
		$(RM) $(OBJS) $(PROG)

```

---

### Post by dwhitney67 on 2010-01-01
Bulls-eye... you placed it in the correct spot.

---

