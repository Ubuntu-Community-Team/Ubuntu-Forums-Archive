---
title: "Why g++ instead of gcc for C++ ?"
date: 2007-10-27
forum: Programming Talk
---

### Post by JupiterV2 on 2007-10-27
After solving my C++ woes via these forums (thank you Ubuntu Community!) I saw a lot of people say that you should use g++ rather than gcc for compiling C++ programs. I didn't see one person say WHY?

Is there more to the story than just having to link the stdc++ (-lstdc++ option) library when using gcc?

---

### Post by LaRoza on 2007-10-27
> **JupiterV2 said:**
> After solving my C++ woes via these forums (thank you Ubuntu Community!) I saw a lot of people say that you should use g++ rather than gcc for compiling C++ programs. I didn't see one person say WHY?

Is there more to the story than just having to link the stdc++ (-lstdc++ option) library when using gcc?

gcc is for C programs, g++ is for C++ programs. Also, g77 is for Fortran 77 programs. There are others that follow the same pattern, like gcl for Common Lisp.

---

### Post by wolfbone on 2007-10-27
From the GCC info pages:

> 3.3 Compiling C++ Programs
==========================

C++ source files conventionally use one of the suffixes `.C', `.cc',
`.cpp', `.CPP', `.c++', `.cp', or `.cxx'; C++ header files often use
`.hh' or `.H'; and preprocessed C++ files use the suffix `.ii'.  GCC
recognizes files with these names and compiles them as C++ programs
even if you call the compiler the same way as for compiling C programs
(usually with the name `gcc').

 However, C++ programs often require class libraries as well as a
compiler that understands the C++ language--and under some
circumstances, you might want to compile programs or header files from
standard input, or otherwise without a suffix that flags them as C++
programs.  You might also like to precompile a C header file with a
`.h' extension to be used in C++ compilations.  `g++' is a program that
calls GCC with the default language set to C++, and automatically
specifies linking against the C++ library.  On many systems, `g++' is
also installed with the name `c++'...

gcl is a CL implementation -  it's not part of the GCC.

---

### Post by Jucato on 2007-10-27
From **man gcc** (or man g++)

> However, programs often require class libraries as well as a compiler that understands the language---and under some circumstances, you might want to compile programs or header files from standard input, or otherwise without a suffix that flags them as programs. You might also like to precompile a C header file with a .h extension to be used in compilations. **g++ is a program that calls GCC with the default language set to , and automatically specifies linking against the library. On many systems, g++ is also installed with the name c++.**

So you could consider g++ as a convenience program calls gcc with the correct options and flags to ensure that the program is compiled as a C++ project.

EDIT:  Bah I was too late. Just an added FYI: GCC is actually the GNU Compiler Collection, not the GNU C Compiler. So yo could also think of g++ as the C++ command for the Collection.

---

### Post by LaRoza on 2007-10-27
> **wolfbone said:**
> 
gcl is a CL implementation -  it's not part of the GCC.

I know, I just pointed out the similarity. (GNU Common Lisp)

---

### Post by JupiterV2 on 2007-10-28
Awesome, I appreciate the excellent information. I'm one of those crazy nuts who like to know WHY something works, not just that it does. =) 

Thanks Ubuntu community members!

---

