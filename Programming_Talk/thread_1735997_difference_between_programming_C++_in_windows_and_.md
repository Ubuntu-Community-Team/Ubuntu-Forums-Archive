---
title: "difference between programming C++ in windows and ubuntu"
date: 2011-04-22
forum: Programming Talk
---

### Post by Mia_tech on 2011-04-22
I learned programming using visual studio, but I would like to use Ubuntu when I do some of my programming; however, I notice when using geany that when I try to do some file i/o code gave me errors when I tried to open a file..... also when I write an object. the member functions that it shows are completely unfamiliar to me... is it the compiler (gcc) that I'm using?

---

### Post by schauerlich on 2011-04-22
What do you expect without providing the code and error messages?

---

### Post by dwhitney67 on 2011-04-22
> **Mia_tech said:**
> I learned programming using visual studio...

I guess there's not much choice under windows

> **Mia_tech said:**
> 
I notice when using geany...

With Linux, you do have a choice.  Why not start to learn how to develop your applications using a simple interface, such as vim or gedit?  Then swoop down to the command line to compile your applications.  You will gain an appreciation of how things work under Linux wrt GCC (g++ for C++ programs).

When you have the confidence of understanding how to build your projects from the command line, then consider using an IDE.


P.S.  I suppose one could follow my suggestion in Windows too, but their DOS shell is crap compared to the power offered by the Linux command line.

---

### Post by cgroza on 2011-04-22
With no error message, our hands are tied.

---

### Post by stchman on 2011-04-22
> **Mia_tech said:**
> I learned programming using visual studio, but I would like to use Ubuntu when I do some of my programming; however, I notice when using geany that when I try to do some file i/o code gave me errors when I tried to open a file..... also when I write an object. the member functions that it shows are completely unfamiliar to me... is it the compiler (gcc) that I'm using?

Can we see your code?

When it comes to console apps there should be no difference.  If you are doing GUI programming then there will be a huge difference.

---

### Post by stchman on 2011-04-22
> **dwhitney67 said:**
> I guess there's not much choice under windows


With Linux, you do have a choice.  Why not start to learn how to develop your applications using a simple interface, such as vim or gedit?  Then swoop down to the command line to compile your applications.  You will gain an appreciation of how things work under Linux wrt GCC (g++ for C++ programs).

When you have the confidence of understanding how to build your projects from the command line, then consider using an IDE.


P.S.  I suppose one could follow my suggestion in Windows too, but their DOS shell is crap compared to the power offered by the Linux command line.

The OP can use actual gcc or g++ if they install Cygwin.  This will also give them a fully functioning terminal as well (after they install the packages).

---

