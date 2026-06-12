---
title: "ddd+jdb woes"
date: 2010-04-15
forum: Programming Talk
---

### Post by help_me_please on 2010-04-15
hi all.
just recently moved to lucid-beta2 from win7.
i do java programming for college and want to use ddd for java debugging.
after looking around i found that this can be done by compiling the java files with java -g <classname> and then running ddd -jdb <classname>.
however i'm having a couple of problems:

* when i run ddd -jdb <classname>, i get an error msg "cannot load <classname>". i finally managed to solve this by setting the classpath to the class directory (which in most my cases is .) by typing "use ." into the console area in ddd. i know i should be able to pass a classpath argument to jdb when launching ddd, but in all ddd+java examples i have found, no1 does this. so i assume there is some problem with my setup and i would like to fix it.

* after starting a debugging session, i can step through instructions just fine. however the display functionality doesn't work at all. this is very important to me - it is the reason i want to use ddd.

i should note that just to be sure, i wrote a test .c file, compiled it with gcc -g and ran it in ddd. all the expected functionality is available when i run ddd with gdb. these problems seem to be jdb-related.

i tried using different both the openjdk-6-jdk and the official jdk off sun's website.

i looked all over the place and can't find any solutions.

help please

---

### Post by help_me_please on 2010-04-16
bump (sorry, urgent)

---

### Post by help_me_please on 2010-04-19
as no-one has been able to help with the problem, i'll change the questions:

1) does anyone know where i can present these problems? the ddd bug tracker seems to have very little activity, so i don't think that's a short term option.

2) does anyone know of a different tool that works with java that provides a feature similar to the memory display that ddd provides?

any help/info is appreciated.

---

### Post by help_me_please on 2010-04-30
bump again - hoping some1 with some useful input might stumble upon this.

---

### Post by Daniil on 2010-04-30
> **help_me_please said:**
> as no-one has been able to help with the problem, i'll change the questions:

1) does anyone know where i can present these problems? the ddd bug tracker seems to have very little activity, so i don't think that's a short term option.


I didn't use ddd with java, but you may read an article in [http://docs.hp.com/en/5992-4687/ch04s07.html](http://docs.hp.com/en/5992-4687/ch04s07.html)
May be it would be helpful.
Do you load a class to ddd with ".class" extension or without? Do you compile with debugging symbols?

> 
2) does anyone know of a different tool that works with java that provides a feature similar to the memory display that ddd provides?

any help/info is appreciated.

Yes, Eclipse :) Install from their site or ubuntu repo.

---

### Post by Vox754 on 2010-04-30
> **help_me_please said:**
> hi all.
just recently moved to lucid-beta2 from win7.
i do java programming for college and **want to use ddd for java debugging**.
after looking around i found that this can be done by compiling the java files with java -g <classname> and then running ddd -jdb <classname>.
however i'm having a couple of problems:

* when i run ddd -jdb <classname>, i get an error msg "cannot load <classname>". i finally managed to solve this by setting the classpath to the class directory (which in most my cases is .) by typing "use ." into the console area in ddd. i know i should be able to pass a classpath argument to jdb when launching ddd, but in all ddd+java examples i have found, no1 does this. so i assume there is some problem with my setup and i would like to fix it.

* after starting a debugging session, **i can step through instructions just fine. however the display functionality doesn't work at all.** this is very important to me - it is the reason i want to use ddd.

i should note that just to be sure, i wrote a test .c file, compiled it with **gcc -g** and ran it in ddd. all the expected functionality is available when i run ddd with gdb. these problems seem to be jdb-related.

i tried using different both the **openjdk-6-jdk** and the official jdk off sun's website.

i looked all over the place and can't find any solutions.

help please
I don't program in Java, however, by reading the GNU debugger documentation ("info" pages in the package "gdb-doc") it seems to me that "gdb" is not supposed to be used with the Java bytecode produced by "javac" from OpenJDK/SunJDK. It seems to me that gdb is primarily used to debug programs compiled in C and C++ because these produce native machine code.

Now, the documentation says it also supports "C, C++, Objective-C, Fortran, Java, Pascal, assembly, Modula-2, and Ada", but I wouldn't trust using ddd for anything else other than C and C++.

Beside OpenJDK/SunJDK there is also GCJ, the GNU Compiler for Java, which last time I heard, is an incomplete implementation of Java 1.4, but which produces native code. I suppose you can try it.

So that's my suggestion, install GCJ, compile with that, and try gdb and ddd, and see if it works. But, if you are using Java 1.5 or 1.6, or any Java for that matter, you shouldn't be looking at GNU tools, you should be looking at Sun's or Oracle's sites to see what tools they have.

---

