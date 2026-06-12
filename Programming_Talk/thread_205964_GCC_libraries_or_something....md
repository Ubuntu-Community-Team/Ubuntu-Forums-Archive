---
title: "GCC libraries or something..."
date: 2006-06-29
forum: Programming Talk
---

### Post by Lster on 2006-06-29
I can get gcc up, but can't compile. I get the following error:

> /tmp/ccZJFc0c.o: (.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

Please help - I'm desperate!

---

### Post by -Rick- on 2006-06-29
Use g++ instead of gcc for cpp files.

---

### Post by thumper on 2006-06-29
did you install gcc or build-essential?

---

### Post by Lster on 2006-06-29
g++ will compile c++. How come gcc doesn't work?

I would still like to use c as well as c++, can i get gcc to work?

I have installed gcc and build-essentials.

---

### Post by thumper on 2006-06-29
You need to give us the full output of the command including the command line you are using to compile.

---

### Post by Lster on 2006-06-29
I use "gcc whateverDirectory/program.c++", the full error is

/tmp/ccZJFc0c.o: (.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

nothing else happens.

---

### Post by asimon on 2006-06-29
If you want this program compiled as C, rename it to whateverDirectory/program.c . Then your gcc command will work.

You can compile c++ programs with gcc too (it detects them through the file extension), but gcc can not link c++ programs, i.e. you can use 'gcc -c hello.cpp' to compile a c++ program into an object file but gcc can't link that object file, you need g++ for this. Thus best use g++ consistently for c++ programs and gcc for C programs.

EDIT: see [An Introduction to GCC: 7.1 Compiling a simple C++ program](http://www.network-theory.co.uk/docs/gccintro/gccintro_54.html).

---

