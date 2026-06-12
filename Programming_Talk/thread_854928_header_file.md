---
title: "header file?"
date: 2008-07-09
forum: Programming Talk
---

### Post by pavel989 on 2008-07-09
somehow this question comes up late after i started learning programming.

Why does C++ have header files and what are they? Why doesn't python or ruby have them. Or do they?

Also, what language are the header files written in?

---

### Post by patryk77 on 2008-07-10
Short answer: You can declare variables and functions inside header files, and call them from the functions you are writing. It allows you to reuse code easily, and gives you access to standard functions, so you don't need to worry about low-level access for files, etc.


[QUOTE=Wikipedia]In computer programming, particularly in the C and C++ programming languages, a header file or include file is a file, usually in the form of source code, that is automatically included in another source file by the compiler. Typically, header files are included via compiler directives at the beginning (or head) of the other source file.

A header file commonly contains forward declarations of subroutines, variables, and other identifiers. Identifiers that need to be declared in more than one source file can be placed in one header file, which is then included whenever its contents are required.

In the C and C++ programming languages, standard library functions are traditionally declared in header files; see C standard library and C++ standard library for examples.[/QUOTE]

[http://en.wikipedia.org/wiki/Header_file](http://en.wikipedia.org/wiki/Header_file)

---

### Post by mssever on 2008-07-10
> **pavel989 said:**
> Why doesn't python or ruby have them. Or do they?
Languages like Python and Ruby don't use header files; they don't need them. Because of the way they're designed, the interpreter has all the access it needs to functions, etc., without resorting to header files.

---

