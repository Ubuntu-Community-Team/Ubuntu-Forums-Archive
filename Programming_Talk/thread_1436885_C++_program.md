---
title: "C++ program"
date: 2010-03-23
forum: Programming Talk
---

### Post by coffeecake on 2010-03-23
say i have a simple C++ program
 
How do i use the make utility to compile my program?

---

### Post by sandyd on 2010-03-23
you can use the g++ or the gcc compiler in the following format.

```

gcc *filename.c*

```
or
```

g++ *filename.c*

```

---

### Post by kleskjr on 2010-03-23
you can use any compiler: g++,gcc, etc.

first write:

g++ program.cpp -o program

and then to run it:

./program

---

### Post by coffeecake on 2010-03-23
No i need to use the MAKE utility of GNU

---

### Post by john newbuntu on 2010-03-23
You can read up any book on creating a basic makefile.  The outline of one simple makefile looks like this although you can add a zillion other options. "pgrm" is your final executable that uses just one source file in this case called x.cpp. A few macros are also used along with targets and dependencies.  Stick these into a file called "makefile" and type "make".

```
CC= g++
OBJS= x.o

pgrm : $(OBJS)
   $(CC) $(OBJS) -o pgrm

x.o: x.cpp
   $(CC) -c x.cpp

clean:
   rm -f $(OBJS) pgrm
```

---

### Post by spanBobHere on 2010-03-31
> **john newbuntu said:**
> You can read up any book on creating a basic makefile.  The outline of one simple makefile looks like this although you can add a zillion other options. "pgrm" is your final executable that uses just one source file in this case called x.cpp. A few macros are also used along with targets and dependencies.  Stick these into a file called "makefile" and type "make".

```
CC= g++
OBJS= x.o

pgrm : $(OBJS)
   $(CC) $(OBJS) -o pgrm

x.o: x.cpp
   $(CC) -c x.cpp

clean:
   rm -f $(OBJS) pgrm
```

ohooo thx a lot. now i can understand the use of (CC) :D

---

### Post by nvteighen on 2010-03-31
Look at this little Make tutorial: [http://crasseux.com/books/ctutorial/Writing-a-makefile.html](http://crasseux.com/books/ctutorial/Writing-a-makefile.html) It's from the GNU C Tutorial; just replace 'gcc' by 'g++' and '.c' by '.cpp' :P Make can be used for any kind of file task where dependencies are needed for control.

---

### Post by napsy on 2010-03-31
You can't use gcc since gcc is a C compiler.

---

### Post by schauerlich on 2010-03-31
> **napsy said:**
> You can't use gcc since gcc is a C compiler.

GCC is the GNU Compiler Collection - it can compile C, C++, Objective-C, and a few other languages. g++ is essentially the same as running "gcc -x c++"

---

### Post by dwhitney67 on 2010-03-31
> **coffeecake said:**
> say i have a simple C++ program
 
How do i use the make utility to compile my program?

Say you have a file called HelloWorld.cpp; the easiest way to generate an executable using 'make' is to use something similar to the following:
```

make HelloWorld

```
This statement will generate an executable with the name 'HelloWorld' using the source file that lives in the current directory, that bears a similar name.  'make' will find your HelloWorld.cpp (or if C code, HelloWorld.c).  It will invoke the appropriate compiler/linker; in the case of C++ code, this is g++.  Contrary to belief, you do *not* require a Makefile to run the command above!

If you want to perform more elaborate tasks using 'make', then your best bet is to create your own Makefile.  Typically this is done if you need to specify special libraries, special include paths, or additional CXXFLAGS.

A simple Makefile would look similar to this:
```

APP  = HelloWorld

SRCS = HelloWorld.cpp
OBJS = $(SRCS:.cpp=.o)

CXXFLAGS = -Wall -pedantic -c

$(APP) : $(OBJS)
<tab>   $(CXX) $^ -o $@

.cpp.o:
<tab>   $(CXX) $(CXXFLAGS) $<

clean:
<tab>   $(RM) $(OBJS) $(APP)

```

---

