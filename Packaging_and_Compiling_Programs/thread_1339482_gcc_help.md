---
title: "gcc help"
date: 2009-11-27
forum: Packaging and Compiling Programs
---

### Post by lewisforlife on 2009-11-27
I need a little clarification with gcc.  Lately I have been playing around with some C programming.  I am using gcc to compile my programs.  I am having trouble knowing what parameters to add to gcc when compiling.  For instance, if I am compiling a program that includes math.h I have to do

```
gcc -o mathprog math.c -lm
```

I don't understand why the "-lm" has to be added to the compiler, why can't it just read math.h.  So, do I have to add a parameter to gcc for every header file I include in the C program?  If so, is there a list with all of these parameters.  For instanance, if I include something.h, how will I know what parameter to add, is it, gcc -lsomething, or gcc -ls.  Is there a list with all of the header files and what -l to add in the gcc code?

Also, what does gcc -Wall do, I notice a lot of examples use -Wall but there is no explanation of what this does?

---

### Post by MadCow108 on 2009-11-29
you don't need to pass headers to gcc, they should be included in the .c files where needed.

compiling and linking are two separate stages which gcc conveniently does in with one call (if wanted).
first gcc compiles your c files. For this it needs to know the signatures of all functions used, that is what headers (.h files) are for.
But the headers rarely contain the implementation of the function (in C at least). The implementation sits in the libraries.
In the linking stage now the compiler searches in the libraries for the implementation of the function signatures needed in your program and adds it all together to a running program.
If it does not find the implementation you get a "undefined reference" error message. This usually means you are missing a library (-l flag)
(you can skip the linking stage by passing the -c flag)

so your math.h just tells the compiler that the math functions exist and how they look like.
the linker needs also know there the implementation of these functions are, so it needs the -lm flag (which tells the linker search for function in the library libm.[library extension] in the default path.


pkg-config is a program which can be useful to find needed flags and libraries of programs.
pkg-config --list-all for a list of registered packages
and then type pkg-config --libs --cflags [package-name] to list the flags


-Wall enables lots of warnings, which is often helpful to find bugs.
You should always compile with at least -Wall and fix all warnings.
more information on what -Wall activates:
man gcc

---

### Post by lewisforlife on 2009-11-30
Wow, thanks for your help.  That was probably the best answer I have ever seen, I think I understand how gcc works now.

Thanks,

---

