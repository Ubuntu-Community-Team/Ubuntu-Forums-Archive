---
title: "Having Trouble with The GCC Compiler"
date: 2010-02-23
forum: Programming Talk
---

### Post by sylar petrelli on 2010-02-23
Hi guys,

I am trying to compile a program that my professor gave me to compile in C. Whenever I try to compile it I keep getting errors that say "undefined reference to". There are multiple things that it does it for. I have all the packages and development tool necessary. But it is still throwing up this error.  I have tried a few threads that talk about linking it. The package, which is GSL is under usr/include. 

What should I do from here?

P.S. Also there are multiple header files that are used in each of these programs.

---

### Post by dwhitney67 on 2010-02-23
An undefined reference error does imply that there was an issue finding one or more functions definitions during the link-stage.

Are you sure that you have linked (compiled) all of the files that are necessary for the project?  Perhaps your application depends on an external library, that you have failed to specify with the gcc command?

Anyways, if you have a moment, please post the exact gcc command you are using, and the output of the errors.  If the error output is very large, then just post the first 10-15 lines.

---

### Post by lloyd_b on 2010-02-23
> **sylar petrelli said:**
> Hi guys,

I am trying to compile a program that my professor gave me to compile in C. Whenever I try to compile it I keep getting errors that say "undefined reference to". There are multiple things that it does it for. I have all the packages and development tool necessary. But it is still throwing up this error.  I have tried a few threads that talk about linking it. The package, which is GSL is under usr/include. 

What should I do from here?

P.S. Also there are multiple header files that are used in each of these programs.

You have the header files (in /usr/include), but do you have the corresponding libraries (in /usr/lib, normally)?

Also, could you provide the actual 'gcc' command line you're using, and tell us exactly which libraries you're using?  It may be that you're just missing a "-l..." directive to let the compiler know that it needs to link in the appropriate library.

Lloyd B.

---

### Post by MadCow108 on 2010-02-23
you need to tell gcc (or better the linker invoked by gcc) which libraries it should link with
undefined reference is an error at the linking stage, so the compiling has already worked.

gsl would be libgsl.someextension. This means add the flag -lgsl to the command line
you don't need lib or the extension
(assuming gsl is installed)

you can also provide a path where it will search for libraries with -Lsomepath

the easier route is available when gsl was installed over a package manager
then compile with:
gcc `pkg-config --libs --cflags gsl` ...
the command pkg-config --libs --cflags gsl (which you can also execute standalone) will print all necessary flags
on my system:
-lgsl -lgslcblas -lm

---

### Post by distortedskies on 2010-02-23
Without a few of the error messages and the command used to compile its hard to say. Whatever library you are trying to link with is not in your linker search path. You can add search paths with the -L flag. So if your library is in /home/libs then try gcc myfile.c -L/home/libs the system librarys will be in /usr/lib or /usr/local/lib

---

### Post by sylar petrelli on 2010-02-23
I found the GSL library it is in usr/lib. 

The command that I am using is "make swarm" for this file, which is swarm.c.

Here are some of the lines.

brian@ubuntu:~/Downloads/swarm_simulation_brian$ make swarm
gcc   swarm.o   -o swarm
/usr/lib/gcc/x86_64-linux-gnu/4.4.1/../../../../lib/crt1.o: In function `_start':
/build/buildd/eglibc-2.10.1/csu/../sysdeps/x86_64/elf/start.S:109: undefined reference to `main'
swarm.o: In function `read_config_file':
swarm.c:(.text+0x95): undefined reference to `params'
swarm.c:(.text+0xc4): undefined reference to `params'
swarm.c:(.text+0xf3): undefined reference to `params'
swarm.c:(.text+0x12c): undefined reference to `params'
swarm.c:(.text+0x165): undefined reference to `params'
swarm.o:swarm.c:(.text+0x194): more undefined references to `params' follow
'


Hope this is helpful.

Thanks a lot.

---

### Post by dwhitney67 on 2010-02-23
In what local file is 'params' defined in?

The following statement seems to imply that you have only one source module (swarm.c) and that the application is not dependent on any external library.
```

gcc swarm.o -o swarm

```

---

### Post by sylar petrelli on 2010-02-23
It is assigned to a file called definitions.h, which is in the same group of files sent. I have tried to compile that and it is giving me one error "undefined reference to main". I have also tried to use variations to link the library. Like 

gcc swarm.c -lgsl swarm

I have also tried to use the direct link to the library. 

gcc -Wall swarm.c /usr/lib/libgsl.a -o swarm

---

### Post by Barrucadu on 2010-02-23
If it has a makefile, have you tried `make all`?

**edit:** is there more than one .c file?

---

### Post by sylar petrelli on 2010-02-23
I did try a makefile there are multiple files. One the first file it stopped at it told me "error: gsl-1.9/gsl/gsl_integration.h: No such file or directory". I located that header file it is under usr/include. 

What should I do now?

---

### Post by MadCow108 on 2010-02-23
undefined reference to main means there is no main function which every executable C program needs.
You need to link with a compiled file which has this main function.

if you're trying to compile a library (which does not have a main function) use the -c flag which skips the link stage

---

### Post by dwhitney67 on 2010-02-23
> **sylar petrelli said:**
> I did try a makefile there are multiple files. One the first file it stopped at it told me "error: gsl-1.9/gsl/gsl_integration.h: No such file or directory". I located that header file it is under usr/include. 

What should I do now?

This is a compiler error (ie. unable to locate a header file).

Sorry to say, but there is not much we can do to fix the problem.  You are going to have to do that yourself.  You may need to fix the source file(s) and possibly the Makefile.

The location of a file, whether it be a header or library, is critical.  Is the gsl_integration.h located under /usr/include or is it /usr/include/gsl-1.9/gsl??

How is it being included within the source file(s)??  This is also important.

What about the Makefile... does it define a CFLAGS variable?  If so, what is it set to?

P.S.  From your earlier post, it is obvious that the CFLAGS is not being used, but I thought I would ask.  Please post your Makefile, if it is not too much trouble.  Use the CODE tags to encapsulate the Makefile.

---

