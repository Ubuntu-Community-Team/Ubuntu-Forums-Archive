---
title: "CMAKE - Link against libraries"
date: 2011-06-28
forum: Programming Talk
---

### Post by m3d_tx on 2011-06-28
Hi all,

I am new to CMake and am somehow lost...

I have a sub-project, which makefile basically is:
```
TARTINE_INCL = /home/me/lib_tartine/include
TARTINE_LIB = -L/home/me/lib -ltata -ltoto -ltutu
all: hello
hello: hello.cpp
    gcc -I$(TARTINE_INCL) -o hello hello.cpp $(TARTINE_LIB)

```

I try to integrate this into a bigger cmake-based project. I "just" want this bigger project to link against this TARTINE library.

Then I did:
```
SET(TARTINE "/home/me/lib_tartine") 
INCLUDE_DIRECTORIES(${TARTINE}/include)
LINK_DIRECTORIES(${TARTINE}/lib)
TARGET_LINK_LIBRARIES( #a bunch of preexisting stuffs
                     ${TARTINE}/lib)
```

When compiling, the include paths are working, but I got some "Undefined reference to ...", which proves that the link did not work...

Thanks for your help,
m.

---

### Post by dwhitney67 on 2011-06-28
I'm not a Cmake user, but it would seem to me that you are missing the specification for the following libraries:```
-ltata -ltoto -ltutu
```

This may very well be the cause of the "undefined references" that the linker is reporting.


P.S.  Your regular Makefile is also incorrect; your TARTINE paths differ, and you should use 'g++', not 'gcc'.

---

### Post by m3d_tx on 2011-06-28
First of all, thanks for your answer.

actually the regular makefile works fine. You're right though my (copy/paste)s failed and one should read:

[LIST]
[*] -L/home/me/lib_tartine/lib instead of -L/home/me/lib
[*]g++ instead of gcc
[/LIST]
Anyway, I've changed the LINK_DIRECTORIES(${TARTINE}/lib) to
```

LINK_DIRECTORIES(
          ${TARTINE}/lib
          ${TARTINE}/lib/libtata.o
          ${TARTINE}/lib/libtoto.o
          ${TARTINE}/lib/libtutu.o
)

```
but actually it changes nothing.
:(

---

