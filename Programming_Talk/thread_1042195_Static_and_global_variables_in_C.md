---
title: "Static and global variables in C"
date: 2009-01-17
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-01-17
Does it make difference if a variable is static or not, when it's declared at the beginning of program?

```

#include <...>
#include "..."

int variable;

...

```
```

#include <...>
#include "..."

static int variable;

...

```

Global variables are bad, and static variables are good. (so I have been told)

But is a static global variable that bad?

---

### Post by GoS_ on 2009-01-17
no, a static global variable isn't necessarily bad. It depends on what you're using it for.  Static simply means that the compiler will make sure that it doesn't get changed anywhere.  If you put it in the global scope it'll always be in memory though.  So a static variable would always be in memory and never change.  If that's what you need, I don't see any problem with it. At least, that's my understanding.

---

### Post by jespdj on 2009-01-17
In C, **static** on global variables detemines the [linkage](http://en.wikipedia.org/wiki/Linkage_(software)) (note that it has a different meaning in other languages such as C++ or Java).

If a global variable is static, then it's only visible inside the compilation unit that it's in, or in other words, the name of the variable is not exported into the object file when it's compiled. You can't access the variable from other compilation units (source files).

Using static on global variables (or functions) is good for things that should remain private inside one source file.

> **GoS_ said:**
> Static simply means that the compiler will make sure that it doesn't get changed anywhere.  If you put it in the global scope it'll always be in memory though.  So a static variable would always be in memory and never change.  If that's what you need, I don't see any problem with it. At least, that's my understanding.
This is incorrect, it sounds like you are confusing static with **const**.

---

### Post by akimatsu123 on 2009-01-17
I'm more familiar with C++, but in C++ they generally have different uses. 

Global variables are variables that are declared so they are accessible anywhere in the program. It's useful, but it can also get messy if there are too many of them hanging around.

A static variable is most commonly used with classes, when you want instances of your classes to have ONE commonly accessed variable, for example to keep a count of how many instances of the class you have created.

Sure, you can accomplish the same thing through global variables, but it's much safer and less error-prone to use a private static variable. 

Hope that made some sense.

---

### Post by crazyfuturamanoob on 2009-01-17
But if the global static variable is in the main program, which doesn't get #included, does it make a difference then?

---

### Post by stroyan on 2009-01-17
Making a global variable static can prevent it from being used by a shared library.  If a shared library declares a non-static global with the same name as one of the main program's non-static globals then they will actually share one variable.

There is also a small performance cost for resolving non-static variables at startup.  The a.out file will include relocation records for those variables that the ld.so dynamic linker/loader needs to read through when looking for symbols to resolve.

---

### Post by JupiterV2 on 2009-01-17
There are few instances where a global variable holds any value over a more secure method of achieving the same goal. It is generally considered better practice to pass variables, either by value or by reference, to functions rather than use a global variable.

Why? Because, especially when using threads, a global variable can be changed by any number of functions. Since threads share access to global variables, an attempt to write and/or read to a global "at the same time" can have very undesirable results.

An example of where it is advantageous to use a global variable is errno. With errno, many functions and libraries may need to check the status of the variable in order to see if an error has occurred and thereby take proper action.

In my experience, there are a very small number of instances where global variables are a good idea or, indeed, necessary.

---

### Post by raghujhu on 2012-12-04
[http://en.wikipedia.org/wiki/Static_variable](http://en.wikipedia.org/wiki/Static_variable)

---

### Post by raghujhu on 2012-12-04
> **GoS_ said:**
> no, a static global variable isn't necessarily bad. It depends on what you're using it for.  Static simply means that the compiler will make sure that it doesn't get changed anywhere.  If you put it in the global scope it'll always be in memory though.  So a static variable would always be in memory and never change.  If that's what you need, I don't see any problem with it. At least, that's my understanding.

I am not sure if you are correct. Static variables can be changed. Look at this wiki link -
[http://en.wikipedia.org/wiki/Static_variable](http://en.wikipedia.org/wiki/Static_variable)

---

### Post by lisati on 2012-12-04
My understanding is that "static" influences what part of the data space (memory, whether or not to use the stack or heap etc) is allocated from, and "global" influences the scope (i.e. what part of the program can access it).

This is an old thread: we usually close old threads that mysteriously come back to life. :(

---

