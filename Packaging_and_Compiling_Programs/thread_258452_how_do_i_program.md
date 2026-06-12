---
title: "how do i program?"
date: 2006-09-16
forum: Packaging and Compiling Programs
---

### Post by Bunto0 on 2006-09-16
hey guys,

i know a bit of c++ and i'm tryign to get back into it. but i don't know where ubuntu's tools are. Namely, how do i compile a c++ or c program, is there a debugger, and are there any sort of "weird things" that i need to know about. 

just think of me as a noob programmer who knows pointers, linked lists, etc. 

maybe someday i can program something for ubuntu :) 

thanks in advance,

Bun2

---

### Post by Christopher Cook on 2006-09-16
C++ requires ALOT of useless coding. You need to work too much. I use python, and can make highly advanced programs, just as advanced as in C/C++. My advice would be to go with Python and ditch C/C++.

---

### Post by rekahsoft on 2006-09-16
To answer your original question you use g++ to compile C++ apps. As for a debugger you will have to go out and take a look.

---

### Post by JuliaChang on 2006-09-17
gcc or g++ can be used to compile C++ programs. I would start with a simpler language like Python, or Perl before learning C++ if you're new.

---

### Post by greeklegend on 2006-10-07
gdb is teh command line debugger. That's in the repos somewhere
Insight is a gui for gdb. That's in the universe section
Just make sure you compile with debugging symbols (g++ -g i think)

---

### Post by hey_ian on 2006-10-08
> **Bunto0 said:**
> hey guys,

i know a bit of c++ and i'm tryign to get back into it. but i don't know where ubuntu's tools are. Namely, how do i compile a c++ or c program, is there a debugger, and are there any sort of "weird things" that i need to know about. 

just think of me as a noob programmer who knows pointers, linked lists, etc. 

maybe someday i can program something for ubuntu :) 

thanks in advance,

Bun2
Ok to answer your question you should use KDevelop. It is in my opinion the best solution for GNU/Linux. In Kdevelop all the GCC tools are combined with a graphical interface, which makes software developing as easy as with MSVS 2005. If you are using Ubuntu you could also use Anjuta, it is a little bit worser but looks better with GNOME.
```
apt-get install kdevelop
```
This only works if the universe channel is enabled.

---

