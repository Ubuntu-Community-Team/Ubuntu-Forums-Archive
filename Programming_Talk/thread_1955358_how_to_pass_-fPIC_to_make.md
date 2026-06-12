---
title: "how to pass -fPIC to make"
date: 2012-04-09
forum: Programming Talk
---

### Post by Pierrick584 on 2012-04-09
Removing all my posts, considering people use this thread to reply  off-topic stuff just to increase their post count, and that admins  doesnt do anything about it.

---

### Post by Bachstelze on 2012-04-09
Typically you would add that to the CFLAGS variable in the Makefile. But that depends how the Makefile is generated (for example if it is generate by autotools, that might be a little more complicated).

---

### Post by Pierrick584 on 2012-04-09
Removing all my posts, considering people use this thread to reply  off-topic stuff just to increase their post count, and that admins  doesnt do anything about it.

---

### Post by dwhitney67 on 2012-04-09
> **Bachstelze said:**
> Typically you would add that to the CFLAGS variable in the Makefile. But that depends how the Makefile is generated (for example if it is generate by autotools, that might be a little more complicated).

Actually, CXXFLAGS for C++ projects, not CFLAGS.

---

### Post by Pierrick584 on 2012-04-09
Removing all my posts, considering people use this thread to reply  off-topic stuff just to increase their post count, and that admins  doesnt do anything about it.

---

### Post by dwhitney67 on 2012-04-09
Personally, I do not use cmake, thus I will not be able to tell everything about it.  However, with a mere Google, I was able to find an example to build a library.

Basically, all I had to do was create a file called CMakeLists.txt; within this file, I added a statements like:
```

add_library(function-static STATIC Function.cpp)

add_library(function SHARED Function.cpp)

```
How you go about setting up your directory structure is up to you, but with my simple experiment, I have something like this, where my library consists of only one source module:
```

$ ls
build/  CMakeLists.txt  Function.cpp  Function.h

```
where I had made the directory build.

Then, I went into the build directory to run cmake, and then make to generate both types of libraries (static and shared-object):
```

$ cd build

$ cmake ..

$ make

```
I hope this helps.

In conclusion, I did not have to concern myself with setting -fPIC, or even playing with CXXFLAGS.  But if I needed to, I'm sure it is documented somewhere with how to specify unique compiler options.  But you need to read, read, read the documentation!

---

