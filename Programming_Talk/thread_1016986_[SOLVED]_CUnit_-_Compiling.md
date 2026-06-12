---
title: "[SOLVED] CUnit - Compiling"
date: 2008-12-20
forum: Programming Talk
---

### Post by jonface on 2008-12-20
I'm having some problems compiling CUnit 2.1 .

I've downloaded the version from sourceforce although I guess there is nothing wrong with the version in the repositrys.

I'm trying to compile one of the examples (CUnit-2.1-0/Examples/AutomatedTest) via,

```

gcc AutomatedTest.c -lcunit -I ../ -I /usr/local/include/CUnit/ 

```

Where ../ is for ExampleTests.h
      /usr/local/include/CUnit/ is for the headers

and libcunit.a is in /usr/local/lib/libcunit.a

The error I'm getting is,

```

/tmp/cco3A09O.o: In function `main':
AutomatedTest.c:(.text+0x180): undefined reference to `print_example_results'
AutomatedTest.c:(.text+0x1c5): undefined reference to `AddTests'
collect2: ld returned 1 exit status

```

So I've had a look for both these functions, they are in ExampleTests.h which is included via AutomatedTest.c .

So I don't get why its not compiling? Ideas?

Thanks.

---

### Post by monkeyking on 2008-12-21
I don't think you can link header files only object code.

---

### Post by jonface on 2008-12-21
I mean I could prefix the include statement with ../ but I checked the man page and this is what it says for -I below. That is not the problem :/ 
Thanks anyway.

```

  -I dir
         Add the directory dir to the list of directories to be
         searched for header files.  Directories named by -I are
         searched before the standard system include directories.
         If the directory dir is a standard system include
         directory, the option is ignored to ensure that the
         default search order for system directories and the
         special treatment of system headers are not defeated .



```

---

### Post by dwhitney67 on 2008-12-21
GCC is compiling your code just fine; what it cannot do is link the source file to form an executable.  Either you are missing a library from your "gcc" statement, or the library you provided (cunit) is missing the function implementations for print_example_results() and AddTests().

P.S.  It could be that within your code, you included calls to the functions above, which do not exist, but generally that you lead you to have a compile error.  Try compiling with the -Wall GCC option to see if the functions have been defined or not.

---

### Post by jonface on 2008-12-21
Argh something you said made me think. I had it in my head if I tell it where the header ExampleTests.h is, it will know where ExampleTests.c is, in the same directory.

I changed the compile line to,

```

 gcc AutomatedTest.c ../ExampleTests.c -lcunit -I ../ -I /usr/local/include/CUnit/

```

(Added the extra ../ExampleTests.c).

It works.

Thanks guys for your help.

Jon.

---

