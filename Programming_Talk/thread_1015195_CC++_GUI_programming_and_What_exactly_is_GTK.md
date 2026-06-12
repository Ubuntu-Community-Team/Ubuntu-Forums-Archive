---
title: "C/C++ GUI programming and What exactly is GTK?"
date: 2008-12-18
forum: Programming Talk
---

### Post by PaulM1985 on 2008-12-18
Hi

This is a bit of a non specific post asking about general programming information regarding GUI.

I program in Java and I have been thinking about programming GUI in C/C++.  I have heard of GTK, but I am unsure of what it is exactly.  Is it a language based on C, or a set of libraries written in C to provide GUI, or neither.  

If you have any advice about GUI programming in C/C++, books, websites etc that would be appreciated.

Paul

---

### Post by kcode on 2008-12-18
> **PaulM1985 said:**
> 
 a set of libraries written in C to provide GUI

That is it! And the language you use to write GUI is also C.
> 
If you have any advice about GUI programming in C/C++, books, websites etc that would be appreciated.


For writing GUI in C++, checkout Qt. Here is the link: [http://trolltech.com/products](http://trolltech.com/products)

----EDIT----
This might also interest you: [http://ubuntuforums.org/showthread.php?t=1013305](http://ubuntuforums.org/showthread.php?t=1013305)

Cheers

---

### Post by StOoZ on 2008-12-18
for GUI with C++ you can also use WxWidgets (=framework), or FLTK , and if you insist on using GTK+ , use the C++ wrapper called : gtkmm

---

### Post by nvteighen on 2008-12-18
GTK+ is, actually, a bunch of libraries (a "framework"?). But it's not a language... it's just C. A programming language is not defined by all functions, but only by the built-ins... and C has, actually, no built-in functions (just types, operators and syntax... the Std. Lib. is a library).

Yes, it's true that GTK+ is such a big abstraction leap that you might ask yourself whether you're still in C or not... when that question assaults you, just look at all the pointers you're using and you'll know where you are :)

---

### Post by Habbit on 2008-12-18
> **nvteighen said:**
>  when that question assaults you, just look at all the pointers you're using and you'll know where you are :)
ROFL!! Indeed. In my opinion, however, C++ with gtkmm is "simpler" (if C++ can be considered simple at all) than good ol' GTK/C. By the way, why are you locked onto C/C++? I mean, GTK has lots of bindings, like PyGTK (Python), which you can combine with Glade to build GUI apps quite fast.

---

### Post by PaulM1985 on 2008-12-18
The reason I have been considering C/C++ GUI is to do with the "executable JAR" debate that happens on here every now and again.  I am comfortable with create programs with Java, but the end user has to have the correct JRE.  

It is not that I am actively looking at moving away from Java, I just wanted to know more about what else is out there and know more about computing in general.  Python is mentioned in this thread, and I am lead to believe by its popularity on this forum that it is very good. But all users need to have the equivalent runtime environment, if that is the right term to use with Python, to run the programs.  With languages like C that is not the case.

Paul

---

### Post by mssever on 2008-12-18
> **PaulM1985 said:**
>  Python is mentioned in this thread, and I am lead to believe by its popularity on this forum that it is very good. But all users need to have the equivalent runtime environment, if that is the right term to use with Python, to run the programs.
Depending on your target environment, that might not be a problem. AFAIK, every modern Linux distro, with the possible exception of some minimalist distros, will already have python as a dependency of something. And I think MacOS also comes with Python. So unless your software needs to run on Windows, you can pretty much assume the Python interpreter is already installed. And it's possible to bottle up a Python script into a Windows executable that includes the interpreter, so you don't have to depend on Python.

---

### Post by bruce89 on 2008-12-18
> **nvteighen said:**
> Yes, it's true that GTK+ is such a big abstraction leap that you might ask yourself whether you're still in C or not... when that question assaults you, just look at all the pointers you're using and you'll know where you are :)

GObject takes a bit of getting used to, but it's quite nice in many respects.

I find Vala quite interesting these days to get round the complexities of GObject in C.

---

### Post by stchman on 2008-12-19
> **PaulM1985 said:**
> Hi

This is a bit of a non specific post asking about general programming information regarding GUI.

I program in Java and I have been thinking about programming GUI in C/C++.  I have heard of GTK, but I am unsure of what it is exactly.  Is it a language based on C, or a set of libraries written in C to provide GUI, or neither.  

If you have any advice about GUI programming in C/C++, books, websites etc that would be appreciated.

Paul

GTK is a windowing toolkit.  Gnome uses GTK.  KDE uses a windowing toolkit called QT.

If you want to create GUIs in GTK you can use an IDE like Glade or Eclips.

---

