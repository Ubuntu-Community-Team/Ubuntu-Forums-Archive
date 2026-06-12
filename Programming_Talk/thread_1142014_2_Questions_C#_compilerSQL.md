---
title: "2 Questions: C# compiler/SQL"
date: 2009-04-28
forum: Programming Talk
---

### Post by gfunkera on 2009-04-28
hi i am looking to learn how to program in c#...
i am familiar with c++ and have experience with visual c++ as well...
i am trying to learn c# because i have been informed that using c# to write a program, one can create, access, and modify databases in mySQL...

I am looking for a good place to start so that i can get at least a bare bones database running at my workplace..

from my understanding, mySQL is the database (i have never used it but im familiar with the commands like SELECT, FROM, etc etc) and the language that the program (the one that reads the mySQL database) is written in c#..

also, do i need to use ASP or PHP?

---

### Post by doas777 on 2009-04-28
ok, 
well the best tools for c# on linux are in mono-develop. it's kinda a weak visual studio clone, but it's getting better all the time.
you can do the tasks you want to perform with most any newish langague, so don;t get locked into the idea that you need to use c# (i love it, but thats just me). 

if you do want to learn about .net langagues, i really suggest you do it on windows, or pick a Linux friendly language like python or java. you can find free versions of all the tools you need for C#/SQL here (for windows): [http://www.microsoft.com/Express/](http://www.microsoft.com/Express/)

---

### Post by directhex on 2009-04-29
Monodevelop is fine for making apps in C#, and you have a choice of compatible database drivers (MySQL, PostgreSQL, SQLite, etc).

If you want to write a webapp, then you'd use ASP.NET - if you want to write a desktop app, use the GUI designer in MonoDevelop to make a GTK# app.

---

### Post by doas777 on 2009-04-29
I love the sig, directhex. vorlon wisdom is pretty heavy.
cheers

---

### Post by jespdj on 2009-04-30
> **gfunkera said:**
> i am trying to learn c# because i have been informed that using c# to write a program, one can create, access, and modify databases in mySQL...
...
from my understanding, mySQL is the database (i have never used it but im familiar with the commands like SELECT, FROM, etc etc) and the language that the program (the one that reads the mySQL database) is written in c#..
You can access a MySQL database from many different programming languages (Java, Python, C, C++, PHP, Ruby, ...), you are not required to use C#.

---

### Post by gtr32 on 2009-04-30
> **jespdj said:**
> You can access a MySQL database from many different programming languages (Java, Python, C, C++, PHP, Ruby, ...), you are not required to use C#.

True. One feature C# does have going for it though is to make XML-files out of datasets easily. I don't know if others have such libraries at disposal but to me that has been very convenient.

---

### Post by directhex on 2009-04-30
> **gtr32 said:**
> True. One feature C# does have going for it though is to make XML-files out of datasets easily. I don't know if others have such libraries at disposal but to me that has been very convenient.

If you want to stick with C#, then you have that option. If you want to use a different language, you have that option (of those listed by jespdj, Python probably has the least vomit-inducing XML support; C or C++ worst).

---

