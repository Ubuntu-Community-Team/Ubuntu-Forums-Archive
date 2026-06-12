---
title: "Help with exe"
date: 2009-11-14
forum: Programming Talk
---

### Post by ctult on 2009-11-14
How can I create Windows .exe files without using Windows?
Also, I want to do the same with Mac .dmgs.

Why I want to do this is because I want to provide an online service for creating programs.

It does not need to be a web programming language.

---

### Post by jdunn on 2009-11-14
There is a compiler I believe is called mingw.
I know that there is an option to use it in the Code::blocks IDE.

**Edit**

You didn't say what programing language but I just assumed C/C++

---

### Post by ctult on 2009-11-14
> **jdunn said:**
> There is a compiler I believe is called mingw.
I know that there is an option to use it in the Code::blocks IDE.

**Edit**

You didn't say what programing language but I just assumed C/C++


It does not matter what programming language.

EDIT: The language has to be open source and cross-platform.

---

### Post by jdunn on 2009-11-14
> **ctult said:**
> It does not matter what programming language.

mingw is in the repositories.

---

### Post by ctult on 2009-11-14
I think this is linux for Windows, not Windows for linux.

---

### Post by ctult on 2009-11-14
would something like AutoIT in wine work?

---

### Post by jdunn on 2009-11-14
> **ctult said:**
> I think this is linux for Windows, not Windows for linux.

It is my understanding that mingw is a GNU C/C++ compiler that allows you to create Windows executables from within linux.  Isn't that what you want?

---

### Post by ctult on 2009-11-14
> **jdunn said:**
> It is my understanding that mingw is a GNU C/C++ compiler that allows you to create Windows executables from within linux.  Isn't that what you want?

Nevermind. I got GCC Windows port (minGW) running in Wine.  It creates Windows executables.:D

---

### Post by The Cog on 2009-11-15
No need for wine (except to test the executable). This is a note I wrote for myself when I first compiled an exe under linux:
> To compile for windows:
install package mingw32
i586-mingw32msvc-gcc -Wall -o thingy.exe thingy.c


---

### Post by ctult on 2009-11-16
Cool!!! Now it is easier and faster for me.

---

