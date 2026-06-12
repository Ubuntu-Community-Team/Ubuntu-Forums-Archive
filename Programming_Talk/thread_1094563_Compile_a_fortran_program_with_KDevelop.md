---
title: "Compile a fortran program with KDevelop"
date: 2009-03-12
forum: Programming Talk
---

### Post by jeneverboy on 2009-03-12
hi
I am used to program with fortran in windows. Now I want to program FORTRAN with KDevelop. The problem is that I dont have any idea how this works in LINUX. Does anyone know a good introduction from the beginning to this? Thanks!

---

### Post by monkeyking on 2009-03-12
Do you need  help setting up kdev to use a fortran compiler?
Or do you need to install a fortran compiler?

---

### Post by jeneverboy on 2009-03-13
Isn't KDevelop a compiler? 

I would like to compile with KDev, if it is possible. Just like you would do with visual in windows. 

Also the makefile-thing isnot clear to me. But I saw that on an other forum topic.

---

### Post by jimi_hendrix on 2009-03-13
> **jeneverboy said:**
> Isn't KDevelop a compiler? 

I would like to compile with KDev, if it is possible. Just like you would do with visual in windows. 

Also the makefile-thing isnot clear to me. But I saw that on an other forum topic.

nonononono

KDevelop and Visual Studios are IDE's, they give you a nice coding environment

they have backend compilers that actually do the compiling...not the IDE itself

---

### Post by monkeyking on 2009-03-13
hmm, ok,
I'll try explain shortly.

Kdevelop is just somekind of glueprogram, that has en texteditor, and this program calls/executes the compiler.
This is  called an ide "integrated dev. environment"
Normally it  contains funky features like,
syntax highlighting, api lookup...


You can write your sourcecode in whatever editor you want.
And then compile it by hand, by typing 
```
gcc yourfile.cpp
```
In a terminal.


Makefiles are just a program  that simply executes a series of compilations, while checking for dependencies in your program.

All compilers as I know  them,
are commandline tools.

The gnu compiler for assembler sourcefiles is called g77.

---

### Post by Shin_Gouki2501 on 2009-03-13
have you heard?
[http://research.sun.com/projects/plrg/faq/index.html](http://research.sun.com/projects/plrg/faq/index.html)


[http://projectfortress.sun.com/Projects/Community](http://projectfortress.sun.com/Projects/Community)


interesting?

---

### Post by jeneverboy on 2009-03-14
ok, 

So in the terminal i can type
gcc *myfilename*.f90 to compile a fortran program.

but then I get this:
gcc: error trying to exec 'f951': execvp: No such file or directory

---

### Post by jeneverboy on 2009-03-14
> gfortran -o executable *myfilename*.f90

creates a executable file named executable. But how do I run this?

---

### Post by monkeyking on 2009-03-14
no not gcc,
I've been using g77 to compile fortran stuff
type```

g77 your file

```

---

### Post by jeneverboy on 2009-03-14
And that makes a .exe right?

And an .exe can be run with Wine (for example) on LINUX systems?

I managed to make an .exe

---

