---
title: "[C++] Questions about writing shared libraries."
date: 2010-06-26
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2010-06-26
First of all is there an easy and good guide about writing a shared library? Something that has simple things like writing a "hello world" lib and expanding on more complex things.

Furthermore I have some questions:
1. When several programs use the same lib, is the lib loaded for each program it needs it or do the different programs "connect" to the same instance of the lib?
2. If the second one happens then that means tha the lib has to allocate new data for each program and have a way to identify them depending on the program, right? Then how does the lib know which set of data(vars/classes etc) to use?
3. Any memory the lib allocates does it get counted as the calling program's memory? Does it add up to the program's memory footprint?

---

### Post by dwhitney67 on 2010-06-26
Unfortunately I do not know of a guide/tutorial that explains how to build a shared-object library, thus I will have to bore you with my petty knowledge.

First of all, one must define the API for the library; this is typically done using one or more header files.  Then, functions must be implemented in source files (ie. .cpp files for C++ projects).

For example, here's a simple header file and implementation file...

MyFunction.h:
```

#ifndef MY_FUNCTION_H
#define MY_FUNCTION_H

void myFunction();

#endif

```
MyFunction.cpp
```

#include "MyFunction.h"

void myFunction()
{
}

```

Once this is complete, each of the .cpp modules is compiled so as create a unique object file.  The most important option to pass the compiler is the -fPIC option. Here's a Makefile that builds the library:
```

LIB      = libmyfnc.so

SRCS     = MyFunction.cpp
OBJS     = $(SRCS:.cpp=.o)

CXXFLAGS = -Wall -pedantic -fPIC

$(LIB): $(OBJS)
        $(CXX) $^ -shared -o $@

.cpp.o:
        $(CXX) $(CXXFLAGS) -c $<

clean:
        $(RM) $(OBJS) $(LIB)

```

That's it.  Running the Makefile (using 'make') will produce a shared-object library called libmyfnc.so.

To use the library with an application, you merely have to include the appropriate header file(s), call the appropriate function(s), and compile/link with the shared-object library.  For example:

Example.cpp:
```

#include "MyFunction.h"

int main()
{
   myFunction();
}

```
To build this app, and this assumes the library is in the current folder:
```

g++ Example.cpp -L./ -lmyfnc -o example

```
Then to run the app:
```

LD_LIBRARY_PATH=./ example

```
If you feel that your library is worthy for everyone (on your system) to use, then you should consider installing it in say, /usr/local/lib.  The header file(s) would be installed in /usr/local/include.  In such a case, you then would not need to use the -L when building an app, nor require the use of LD_LIBRARY_PATH when running the app.  Of course this assumes that /usr/local/include is in your ldconfig cache.

As for your other questions (namely #1 and #3), each application runs within its own program space.  It references a library as needed during runtime, and memory allocations, if any, are done for each application that utilizes the library.

As for your question #2, I have no idea what you are asking.

---

### Post by SledgeHammer_999 on 2010-06-26
Thank you. I understood many things now. About #2 question.

Let's say that the lib has to functions: init(), print_contents(). The user has to call init() to initialize the lib. The init function creates an instance of an internal class that contains many things. The print_contents() just prints the contents of the class instance I mentioned above. This is straight-forward if the lib is used by one program. My concern is what happens if multiple programs connect to the same library? If program A calls init() and program B calls print_contents() will the lib use the instance created in A's init() or will it fail in B(since it hasn't call init() which creates the instance)?

---

### Post by pbrane on 2010-06-26
Each process is run in it's own virtual address space. It behaves as if it is the only process running on the machine. So if your program needs a shared library it is loaded in the virtual address space of the calling program. If another program needs the same library it is loaded in it's process's virtual address space.

maybe this will help:
[http://en.wikipedia.org/wiki/Virtual_memory]("http://en.wikipedia.org/wiki/Virtual_memory")

---

### Post by dwhitney67 on 2010-06-26
As I mentioned earlier, each program runs within its own program space.  The data used by one program will not be visible by another (unless shared-memory is used between the two).

As for having free-floating C-style functions in a C++ library, well that just makes me cringe.

Initialization should take place in a class constructor; and printing class values should be handled by an operator<<() method.

---

### Post by Can+~ on 2010-06-26
In short:

1. The library is loaded into memory the first time is needed, subsequent requests will be redirected to the said memory page(s).

2. Shared libraries don't store anything. In fact, no library stores anything, when you use a library, anything that you instantiate from their definitions, is used on your memory space, and your memory space alone.

A shared object is not like a running application, it is that, a library, **it just describes how to do things, it doesn't store them**.

3. The only thing you reduce with shared objects is memory used by having the code up in memory (and well, the costs of getting it there), if there are many required instances of that code.

---

### Post by nvteighen on 2010-06-27
When you write a program, the desirable design is one that makes each part relie on other parts, combining and extending them. That's called modularity and I guess you already know it.

Ok, libraries (shared or static) are just those procedures and data structures you would consider to be the building blocks for something. It's irrelevant whether those procedures and structures are coded "inside" your program or linked by the compiler at compile-time (static) or linked by the compiler to load them at run-time (shared).

What I mean is that your style of coding shouldn't be different: all programs should be considered to be formed by internal "libraries". The only difference is the availability of that code for other new programs, i.e. a technical, not a conceptual problem.

---

### Post by SledgeHammer_999 on 2010-06-27
Well thank you all. I think I fully understand the concept now. I was confused because I had seen some libraries(can't remember which) that had an initilization function that returned a "handler". Then you had to pass that handler to any subsequent call to a function of the lib. So I assumed that this handler was used to indentify the different sets of data ie it was used by the library to identify which program made the call. Which of course is wrong. Probably it was used for some other purpose.

---

