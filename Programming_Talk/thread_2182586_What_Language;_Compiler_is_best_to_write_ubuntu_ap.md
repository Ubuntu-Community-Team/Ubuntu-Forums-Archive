---
title: "What Language; Compiler is best to write ubuntu application"
date: 2013-10-21
forum: Programming Talk
---

### Post by mpskinner on 2013-10-21
Hi

I am interested in learning to write an application for ubuntu. What advice wuould you give on the language compiler I need to use. I want only open source.


Just as a matter of interest what is complied with. ?

thank you...

---

### Post by oldos2er on 2013-10-21
Moved to Programming Talk.

---

### Post by Bachstelze on 2013-10-21
>  Just as a matter of interest what is complied with. ?

?

---

### Post by King Dude on 2013-10-21
If you'd like to program an application for Ubuntu, I suggest learning C++. Here's what you need:

Compiler: [GCC]("http://gcc.gnu.org/")
IDE: [Code::Blocks]("http://www.codeblocks.org/")

[Tutorial]("http://www.cplusplus.com/doc/tutorial/")

---

### Post by mpskinner on 2013-10-21
Thx King Dude... Good Links....

---

### Post by mpskinner on 2013-10-22
Oh.. What is ubuntu complied with? my mistake

---

### Post by ofnuts on 2013-10-22
Ubuntu is a Linux kernel and a collection of applications. The kernel is mostly C., for the rest, I just collated some data from my workstation:

- 4800 executables files and 3700 libraries under /user. Libraries are likely C/C++(*)
- 2100 executables have a shebangn and are interpreted. The other 2700 are therefore binaries, likely C/C++(*).
- In these 2100, roughly one half are shell scripts (sh/bash/tcsh), one fourth are python, and one fourth are perl, and some various (ruby, awk, make...)

(*) of course I didn't check the source files..

---

### Post by edouardtavinor on 2013-10-22
Ubuntu is mostly compiled with GCC (the parts of it that are compiled, that is). Out of the box, it comes with interpreters for at least Perl, Python and awk. As well as this it has a shell (the bash shell).

I have no idea what Unity is written in, but I seem to remember it using lots of Python. This means that it runs without being compiled. The windowing server (the basic part of the graphical interface which talks to the kernel and the hardware) is written in C, and the kernel (Linux) is mostly written in C, with some Perl and shell scripts, if I remember correctly.

If you want to write a graphical application for Ubuntu, you can use any language which has bindings to the basic libraries of which ever desktop environment you have installed. Or you can just write for the XServer directly and bypass the desktop environment.

Confused? You should be.

I'd recommend starting out in python. There are some good tutorials for Ubuntu graphical application development in Python. You can start here: [http://developer.ubuntu.com/resources/programming-languages/python/](http://developer.ubuntu.com/resources/programming-languages/python/)

Good luck!

---

### Post by Bachstelze on 2013-10-22
> **mpskinner said:**
> Oh.. What is ubuntu complied with? my mistake

Ubuntu is not a program, it is a large collection of programs put together, which are programmed in a wide variety of languages. The compiler is, at least in principle, irrelevant: a program written in a language can be compiled with any compiler for that language.

---

### Post by GeneralZod on 2013-10-23
> **edouardtavinor said:**
> 
I have no idea what Unity is written in, but I seem to remember it using lots of Python. 

Unity is mostly C++:

[http://www.ohloh.net/p/ubuntu-unity/analyses/latest/languages_summary](http://www.ohloh.net/p/ubuntu-unity/analyses/latest/languages_summary)

---

