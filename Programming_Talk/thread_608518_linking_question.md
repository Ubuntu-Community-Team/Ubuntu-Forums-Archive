---
title: "linking question"
date: 2007-11-10
forum: Programming Talk
---

### Post by queency on 2007-11-10
Hi guys:

when i: g++ main.cc databaseWrap.cc /usr/lib/libsqlite3.so.0 
everythink compiled and linked ok !

when i gcc main.cc databaseWrap.cc
all compiled ok!

when i:ld main.o databaseWrap.o /usr/lib/libstdc++.so.6 /usr/lib/libsqlite3.so.0

ld: warning: cannot find entry symbol _start; defaulting to 0000000000400848
main.o: In function `__static_initialization_and_destruction_0(int, int)':
main.cc:(.text+0x28): undefined reference to `__dso_handle'

what is wrong with my linkage section ??

Hi guys:

when i: g++ main.cc databaseWrap.cc /usr/lib/libsqlite3.so.0 
everythink compiled and linked ok !

when i gcc main.cc databaseWrap.cc
all compiled ok!

when i:ld main.o databaseWrap.o /usr/lib/libstdc++.so.6 /usr/lib/libsqlite3.so.0

ld: warning: cannot find entry symbol _start; defaulting to 0000000000400848
main.o: In function `__static_initialization_and_destruction_0(int, int)':
main.cc:(.text+0x28): undefined reference to `__dso_handle'

what is wrong with my linkage section ??

---

### Post by smartbei on 2007-11-10
Not sure about actual problem, but please fix a few things in your formatting to help other readers:
[LIST=1]
[*]Why does the same text appear twice in your post? (Copy and paste twice???)
[*]Please use the quote and/or code tags to enclose code (See the # symbol in the "advanced" editor for example).
[*]Please remove smilies from your post by checking that option under "Miscellaneous Options" when posting or editing "advanced"
[/LIST]

EDIT: Maybe I do have an idea about the actual problem (might be wrong though - this is just from googling a bit):

I think you are missing a -o option in your linking command. You have:
```

ld main.o databaseWrap.o /usr/lib/libstdc++.so.6 /usr/lib/libsqlite3.so.0

```
According to [http://www.gnu.org/software/binutils/manual/ld-2.9.1/html_mono/ld.html#SEC3](http://www.gnu.org/software/binutils/manual/ld-2.9.1/html_mono/ld.html#SEC3) It should be in the format:
```

ld -o output /lib/crt0.o hello.o

```
Try adding the -o.

---

### Post by hod139 on 2007-11-10
> **queency said:**
>  when i: g++ main.cc databaseWrap.cc /usr/lib/libsqlite3.so.0 
everythink compiled and linked ok !

when i gcc main.cc databaseWrap.cc
all compiled ok!

Why are you switching between gcc and g++?  Use g++ for C++ code and gcc for C code.  Also, try using g++ for the linking.

---

### Post by Kadrus on 2007-11-10
Euuh..GCC doesn't compile C++..
Try using Anjuta for C++..I don't think you will have any probs..

---

### Post by Compyx on 2007-11-10
> **Kadrus said:**
> Euuh..GCC doesn't compile C++..
Try using Anjuta for C++..I don't think you will have any probs..

GCC does compile C++, just call the C++ front-end of GCC with g++ and the C front-end with gcc. GCC stands for the GNU Compiler Collection. And what do you think Anjuta calls when you ask it to compile C++ code? Yep: GCC's C++ compiler: g++. It also uses the GNU Autotools to set up makefiles so you can compile and link properly.

As soon as I have more than one source file, or if I need to link against a library, I use a makefile. That's what the OP should do, along with using [code] tags around the commands and their output.

---

### Post by the_unforgiven on 2007-11-10
> **queency said:**
> Hi guys:

when i: g++ main.cc databaseWrap.cc /usr/lib/libsqlite3.so.0 
everythink compiled and linked ok !

when i gcc main.cc databaseWrap.cc
all compiled ok!

when i:ld main.o databaseWrap.o /usr/lib/libstdc++.so.6 /usr/lib/libsqlite3.so.0

ld: warning: cannot find entry symbol _start; defaulting to 0000000000400848
main.o: In function `__static_initialization_and_destruction_0(int, int)':
main.cc:(.text+0x28): undefined reference to `__dso_handle'

what is wrong with my linkage section ??


You might want to study the output of:
```
g++ **-v** main.cc databaseWrap.cc /usr/lib/libsqlite3.so.0
```
The -v option tells GCC to be verbose about each step that it carries out - so you can see all the compilation steps separated. Just take a look at the step that calls collect2 - the GCC linker which internally calls ld.so.2 - the dynamic linker/loader.
HTH ;)

---

### Post by queency on 2007-11-10
thanks very much for all that respond 
i will surelly use the -v option next time i GCC
g++ compiles and links OK

Another thing :

I have added the library sqlite3 in the Project Properties Package (Anjuta)

Anjuta 2.2.0  compile my project properly 
But
Doesn't link the Project
I think it uses Make and i don't know how to handle make yet.

Does Anjuta have bugs ?

---

### Post by NathanB on 2007-11-10
> **Kadrus said:**
> Euuh..GCC doesn't compile C++..
Try using Anjuta for C++..I don't think you will have any probs..

Nonsense.  The command "gcc" looks at the extension of the files being passed to it to determine which back-end language compiler to use.  Issue the following command to learn how many languages are supported by gcc:

```
  $ man gcc

```

```
  regular C code...
  $ gcc -o myprog myprog.c

  some C++ code...
  $ gcc -o myplusplus myplusplus.C

  a C++ program which includes a C module...
  $ gcc -o MultiLangDemo plusplus.C module.c

```

---

### Post by dwhitney67 on 2007-11-10
NathanB -

What GCC compiler are you using?  I have gcc-4.1.2.

When I try to compile this simple program:

```
#include <iostream>

int main()
{
  std::cout << "hello world" << std::endl;
}
```

with gcc, in the following manner:

```
gcc hello.cpp
```

I get these errors:

```
/tmp/cca3FKCL.o: In function `__static_initialization_and_destruction_0(int, int)':
hello.cpp:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/cca3FKCL.o: In function `__tcf_0':
hello.cpp:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cca3FKCL.o: In function `main':
hello.cpp:(.text+0x8e): undefined reference to `std::cout'
hello.cpp:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
hello.cpp:(.text+0x9b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
hello.cpp:(.text+0xa3): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/cca3FKCL.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

You claim that gcc works when compiling C++ programs, and even stated that it was "nonsense" what someone had written earlier (that gcc is for C programs, g++ for C++).  Do you care to elaborate?

---

### Post by dwhitney67 on 2007-11-10
> **queency said:**
> thanks very much for all that respond 
i will surelly use the -v option next time i GCC
g++ compiles and links OK

Another thing :

I have added the library sqlite3 in the Project Properties Package (Anjuta)

Anjuta 2.2.0  compile my project properly 
But
Doesn't link the Project
I think it uses Make and i don't know how to handle make yet.

Does Anjuta have bugs ?

Did you ever try compiling/linking as follows:

```
$ g++ main.cc databaseWrap.cc -l sqlite3
```

---

### Post by NathanB on 2007-11-10
> **dwhitney67 said:**
> NathanB -

What GCC compiler are you using?  I have gcc-4.1.2.

When I try to compile this simple program:

```
#include <iostream>

int main()
{
  std::cout << "hello world" << std::endl;
}
```

with gcc, in the following manner:

```
gcc hello.cpp
```

I get these errors:

```
/tmp/cca3FKCL.o: In function `__static_initialization_and_destruction_0(int, int)':
hello.cpp:(.text+0x23): undefined reference to `std::ios_base::Init::Init()'
/tmp/cca3FKCL.o: In function `__tcf_0':
hello.cpp:(.text+0x6c): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cca3FKCL.o: In function `main':
hello.cpp:(.text+0x8e): undefined reference to `std::cout'
hello.cpp:(.text+0x93): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
hello.cpp:(.text+0x9b): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::endl<char, std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&)'
hello.cpp:(.text+0xa3): undefined reference to `std::basic_ostream<char, std::char_traits<char> >::operator<<(std::basic_ostream<char, std::char_traits<char> >& (*)(std::basic_ostream<char, std::char_traits<char> >&))'
/tmp/cca3FKCL.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

```

You claim that gcc works when compiling C++ programs, and even stated that it was "nonsense" what someone had written earlier (that gcc is for C programs, g++ for C++).  Do you care to elaborate?


Then, evidently, *you* need to read the gcc man page.  Here are some significant snippets of said document:

```

NAME
       gcc - GNU project C and C++ compiler

...

       Most of the command line options that you can use with GCC are useful
       for C programs; when an option is only useful with another language
       (usually C++), the explanation says so explicitly.  If the description
       for a particular option does not mention a source language, you can use
       that option with all supported languages.

...

       Options Controlling the Kind of Output

       Compilation can involve up to four stages: preprocessing, compilation
       proper, assembly and linking, always in that order.  GCC is capable of
       preprocessing and compiling several files either into several assembler
       input files, or into one assembler input file; then each assembler
       input file produces an object file, and linking combines all the object
       files (those newly compiled, and those specified as input) into an exe&#8208;
       cutable file.

       For any given input file, the file name suffix determines what kind of
       compilation is done:

       file.c
           C source code which must be preprocessed.

       file.i
           C source code which should not be preprocessed.

       file.ii
           C++ source code which should not be preprocessed.

       file.m
           Objective-C source code.  Note that you must link with the libobjc
           library to make an Objective-C program work.

       file.mi
           Objective-C source code which should not be preprocessed.

       file.mm
       file.M
           Objective-C++ source code.  Note that you must link with the
           libobjc library to make an Objective-C++ program work.  Note that
           .M refers to a literal capital M.

       file.mii
           Objective-C++ source code which should not be preprocessed.

       file.h
           C, C++, Objective-C or Objective-C++ header file to be turned into
           a precompiled header.

       file.cc
       file.cp
       file.cxx
       file.cpp
       file.CPP
       file.c++
       file.C
           C++ source code which must be preprocessed.  Note that in .cxx, the
           last two letters must both be literally x.  Likewise, .C refers to
           a literal capital C.

       file.hh
       file.H
           C++ header file to be turned into a precompiled header.

       file.f
       file.for
       file.FOR
           Fortran source code which should not be preprocessed.

       file.F
       file.fpp
       file.FPP
           Fortran source code which must be preprocessed (with the tradi&#8208;
           tional preprocessor).

       file.r
           Fortran source code which must be preprocessed with a RATFOR pre&#8208;
           processor (not included with GCC).

       file.f90
       file.f95
           Fortran 90/95 source code which should not be preprocessed.

       file.ads
           Ada source code file which contains a library unit declaration (a
           declaration of a package, subprogram, or generic, or a generic
           instantiation), or a library unit renaming declaration (a package,
           generic, or subprogram renaming declaration).  Such files are also
           called specs.

       file.adb
           Ada source code file containing a library unit body (a subprogram
           or package body).  Such files are also called bodies.

       file.s
           Assembler code.

       file.S
           Assembler code which must be preprocessed.

       other
           An object file to be fed straight into linking.  Any file name with
           no recognized suffix is treated this way.

       You can specify the input language explicitly with the -x option:

       -x language
           Specify explicitly the language for the following input files
           (rather than letting the compiler choose a default based on the
           file name suffix).  This option applies to all following input
           files until the next -x option.  Possible values for language are:

                   c  c-header  c-cpp-output
                   c++  c++-header  c++-cpp-output
                   objective-c  objective-c-header  objective-c-cpp-output
                   objective-c++ objective-c++-header objective-c++-cpp-output
                   assembler  assembler-with-cpp
                   ada
                   f77  f77-cpp-input  ratfor
                   f95
                   java
                   treelang

       -x none
           Turn off any specification of a language, so that subsequent files
           are handled according to their file name suffixes (as they are if
           -x has not been used at all).

...

       If you only want some of the stages of compilation, you can use -x (or
       filename suffixes) to tell gcc where to start, and one of the options
       -c, -S, or -E to say where gcc is to stop.  Note that some combinations
       (for example, -x cpp-output -E) instruct gcc to do nothing at all.

...

       Compiling C++ Programs

       C++ source files conventionally use one of the suffixes .C, .cc, .cpp,
       .CPP, .c++, .cp, or .cxx; C++ header files often use .hh or .H; and
       preprocessed C++ files use the suffix .ii.  GCC recognizes files with
       these names and compiles them as C++ programs even if you call the com&#8208;
       piler the same way as for compiling C programs (usually with the name
       gcc).

       However, C++ programs often require class libraries as well as a com&#8208;
       piler that understands the C++ language---and under some circumstances,
       you might want to compile programs or header files from standard input,
       or otherwise without a suffix that flags them as C++ programs.  You
       might also like to precompile a C header file with a .h extension to be
       used in C++ compilations.  g++ is a program that calls GCC with the
       default language set to C++, and automatically specifies linking
       against the C++ library.  On many systems, g++ is also installed with
       the name c++.

```

**  the GPL [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) applies to the above quoted text **

Nathan.

---

### Post by NathanB on 2007-11-10
You can test this feature with this file:

```

int main()
{
  return 42;
}

```

Save as "helloplus.C" and compile like so:

```

$ gcc -o helloplus helloplus.C

```

Yes, it _is_ just a **technicallity**, but...   it is always a "good thing" to learn how these tools REALLY work.

---

### Post by dwhitney67 on 2007-11-10
NathanB -

I think you are missing the bigger picture here.  The GCC statement that you used WILL NOT compile the program sample I provided earlier.... you know, the one with actual C++ statements in it.  The sample you provided is a simple C program.

Anyhow, the ball's back in your court.

---

### Post by dwhitney67 on 2007-11-10
I just found out how to compile a C++ program using gcc.  The syntax is

```
$ gcc file.cpp -lstdc++
```

Slightly different from just:

```
$ gcc file.cpp
```

---

### Post by LaRoza on 2007-11-11
> **dwhitney67 said:**
> I just found out how to compile a C++ program using gcc.  The syntax is

```
$ gcc file.cpp -lstdc++
```


Or ```
g++ file.cpp
```

---

### Post by NathanB on 2007-11-11
> **dwhitney67 said:**
> NathanB -

I think you are missing the bigger picture here.  The GCC statement that you used WILL NOT compile the program sample I provided earlier.... you know, the one with actual C++ statements in it.  The sample you provided is a simple C program.

Anyhow, the ball's back in your court.

We see that you have failed to read the entire text:

```

       Compiling C++ Programs

       C++ source files conventionally use one of the suffixes .C, .cc, .cpp,
       .CPP, .c++, .cp, or .cxx; C++ header files often use .hh or .H; and
       preprocessed C++ files use the suffix .ii.  GCC recognizes files with
       these names and compiles them as C++ programs even if you call the com&#8208;
       piler the same way as for compiling C programs (usually with the name
       gcc).

       However, C++ programs often require class libraries as well as a com&#8208;
       piler that understands the C++ language---and under some circumstances,
       you might want to compile programs or header files from standard input,
       or otherwise without a suffix that flags them as C++ programs.  You
       might also like to precompile a C header file with a .h extension to be
       used in C++ compilations.  g++ is a program that calls GCC with the
       default language set to C++, and automatically specifies linking
       against the C++ library.  On many systems, g++ is also installed with
       the name c++.

```

** the GPL [http://www.gnu.org/copyleft/gpl.html](http://www.gnu.org/copyleft/gpl.html) applies to the above quoted text **

---

