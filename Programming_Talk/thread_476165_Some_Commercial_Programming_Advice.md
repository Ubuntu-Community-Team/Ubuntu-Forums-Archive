---
title: "Some Commercial Programming Advice"
date: 2007-06-16
forum: Programming Talk
---

### Post by thomasaaron on 2007-06-16
I would like to write an application that could be commercially distributed for use on both Linux and Windows machines.

I thought I had it all figured out (creating the .exe file for Windows with py2exe and creating an installer with Inno Setup), that is, until I learned that py2exe forks the MSVCR71.dll from Python, making commercial distribution of programs frozen with py2exe illegal (at least as far as I can understand). And paying some sort of licensing fee to Microsoft is not something I can afford or am interested in.

I know I could have end users download Python and then sell them my application. But I've got doubts about how well that would go over with Windows users. I'm not concerned about distributing to Linux users, as they will have no problem downloading Python (if they don't already have it).

My questions are:

1. Does anybody know if anything has changed with the legality of re-distributing MSVCR71.dll.

2. Is there another cross-platform language that meets the following requirements:
[LIST]
[*]The source and necessary libraries can be converted to a .exe file
[*]Is capable of using either Tk or GTK for GUI's
[*]Can be packaged with for distribution and installation with Inno Settup
[*]Doesn't infringe on the proprietary sensibilities of M$
[/LIST]

Does Ruby fit these qualifications?

Note: I really don't want to use C/C++, as it would drag out the development in ways that I do not have the time/skill for.

---

### Post by kknd on 2007-06-17
There is. A functional language called Haskell.

Has a excelent gtk+ binding, and can be compiled into a binary executable, that doesnt need a virtual machine to run, and is portable. You will only neeed the GTK+ preinstaled.

But there is no need for it. You can still sell your product showing the source code.

---

### Post by Smygis on 2007-06-17
Perhaps **D** is for you, I dont realy know a lot about the language and its realy freash. I looked a bit on some code and it looks nice.

[www.digitalmars.com/d/](www.digitalmars.com/d/)

Perhaps pyinstaller is what you want.
[http://pyinstaller.hpcf.upr.edu/cgi-bin/trac.cgi](http://pyinstaller.hpcf.upr.edu/cgi-bin/trac.cgi)

---

### Post by nitro_n2o on 2007-06-17
Lot's of people nowadays use Java for commercial application programming... clean and easy to use, it might not be really the best for linux

---

### Post by thomasaaron on 2007-06-17
> There is. A functional language called Haskell. Has a excelent gtk+ binding, and can be compiled into a binary executable, that doesnt need a virtual machine to run, and is portable. You will only neeed the GTK+ preinstaled.

That's interesting. I was looking at a book on Haskell at the book store last night.
I'll do some more research on that. Does it have good libraries and the ability to interface with SQL databases?

> Perhaps pyinstaller is what you want.
[http://pyinstaller.hpcf.upr.edu/cgi-bin/trac.cgi](http://pyinstaller.hpcf.upr.edu/cgi-bin/trac.cgi)

That had me pretty excited, but then I found this.
[http://pyinstaller.hpcf.upr.edu/cgi-bin/trac.cgi/roadmap](http://pyinstaller.hpcf.upr.edu/cgi-bin/trac.cgi/roadmap)
It looks like they are working on it, though.

> 
Lot's of people nowadays use Java for commercial application programming... clean and easy to use, it might not be really the best for linux.

Now, will Java work for stand-alone applications that are not dependent on the Internet. In other words, I want people to be able to fire it up from their applications/programs.

---

### Post by nitro_n2o on 2007-06-17
> **thomasaaron said:**
> 
Now, will Java work for stand-alone applications that are not dependent on the Internet. In other words, I want people to be able to fire it up from their applications/programs.

Yes, as long as they have the JRE installed on their systems. In windows you can convert Java programmers to exe using some commercial tools... 
[http://www.google.com/search?q=java+to+exe&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=java+to+exe&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by nitro_n2o on 2007-06-17
> **kknd said:**
> There is. A functional language called Haskell.

Has a excelent gtk+ binding, and can be compiled into a binary executable, that doesnt need a virtual machine to run, and is portable. You will only neeed the GTK+ preinstaled.

But there is no need for it. You can still sell your product showing the source code.

But!! Functional programming is PAIN isn't it :(

---

### Post by pmasiar on 2007-06-17
> **nitro_n2o said:**
> Lot's of people nowadays use Java for commercial application programming... clean and easy to use, it might not be really the best for linux

Not exactly. Lot of *enterprises* use Java as main language, if they need to coordinate hundreds of programmers in complex projects.

But for small projects java is overkill. And for startups too. Just guess that language used YouTube? Hint: *not* java. :-)

---

### Post by kknd on 2007-06-17
> **thomasaaron said:**
> Does it have good libraries and the ability to interface with SQL databases?

There is some libs that deal with databases, but Haskell dont have 1 % of the libraries that Java/C++ has.

[QUOTE=nitro_n2o]
But!! Functional programming is PAIN isn't it
[/QUOTE]


No, its hard to do the usual things that are done easily in Java, but there is a lot of things that you can do much better (can you imagine a quicksort with two lines?).

There is a game (freetennis) written in a functional language (OCalm).

---

### Post by Jessehk on 2007-06-17
Have you considered Ocaml? It has a lot of the benefits of Haskell but it has a much less steep learning curve (side effects are allowed). 

It emphasizes speed (it's about as fast as C), and safety (at has a **very** strong type system). It has a variety of development tools, and it's open source.

Take a look. :)

---

### Post by pmasiar on 2007-06-17
> **kknd said:**
> There is some libs that deal with databases, but Haskell dont have 1 % of the libraries that Java/C++ has.

Get mainstream dynamically typed language - get Python. You have flexibility of functional programming and access to vast pool of libraries.

And yes, Python is multi-paradigm language, you can use  many  tricks of functional programming, like lambda, generator expressions, *very* flexible list processing, dynamic changes of classes ("monkey-patching") etc. And as bonus you have less braces/parenthes to count. :-)

> can you imagine a quicksort with two lines?).

Yes. It should be one line: standard library call :-)

---

### Post by kknd on 2007-06-17
> **pmasiar said:**
> Get mainstream dynamically typed language - get Python. You have flexibility of functional programming and access to vast pool of libraries.

...


Yes, I know the functional things borrowed from the functional world =), but Haskell is a pure functional language.

And GHC (main compiler for Haskell) compiles into C-- (C, but using a very short list of keywords), and is 30x faster than Python, and dont depend on any virtual machine.

I like Python too, and I am not telling that Haskell is better, because its two very different languages, with different proposes.

---

