---
title: "Which coding language is the fittest for the future?"
date: 2012-07-31
forum: Programming Talk
---

### Post by iDuck on 2012-07-31
I already know HTML5, CSS and a bit PHP. Know I would like to begin to program some (Desktop) apps for Ubuntu or in general programs for Ubuntu.

Well, now I would like to know which coding language is the fittest for the future. Which one should I start to learn?

regards,
iDuck

PS: I wanted to add a poll to this thread but I can't find the option to add one. So if there is a Moderator or Administrator who reads this I would be please if he could add a poll with some coding languages like C++ or Java. Thanks.

---

### Post by Elfy on 2012-07-31
> **iDuck said:**
> I already know HTML5, CSS and a bit PHP. Know I would like to begin to program some (Desktop) apps for Ubuntu or in general programs for Ubuntu.

Well, now I would like to know which coding language is the fittest for the future. Which one should I start to learn?

regards,
iDuck

PS: I wanted to add a poll to this thread but I can't find the option to add one. So if there is a Moderator or Administrator who reads this I would be please if he could add a poll with some coding languages like C++ or Java. Thanks.

The only place you can start a poll is in the Cafe.

Moved.

---

### Post by iDuck on 2012-08-01
Anyone who can help me?

---

### Post by Lars Noodén on 2012-08-01
The language you choose is mostly going to be determined by what you are planning on doing.  What do you want to do?

---

### Post by Simian Man on 2012-08-01
You didn't give a whole lot of info, but Python is a great language that is pretty well adaptable to most tasks.  And it has lots of tools and libraries available on Linux.

---

### Post by Dakaa on 2012-08-02
> **iDuck said:**
> I already know HTML5, CSS and a bit PHP. Know I would like to begin to program some (Desktop) apps for Ubuntu or in general programs for Ubuntu.

Well, now I would like to know which coding language is the fittest for the future. Which one should I start to learn?

regards,
iDuck

PS: I wanted to add a poll to this thread but I can't find the option to add one. So if there is a Moderator or Administrator who reads this I would be please if he could add a poll with some coding languages like C++ or Java. Thanks.

HTML5, CSS are not considered as coding language tbh, I started off learning programming starting from JAVA 2 years ago, it's fun once you understand how the basics work but can get redundant and boring sometimes, now I'm just doing C, C#, assembly code, at a basic high-level stuff. I can upload my lecture and assignment contents in a zip if you want, because most of the "tutorials" you found on Google, they usually don't mention tiny little things that matters sometimes when you program they only guide you on general stuff if you know what I mean. And this forum is awesome...

---

### Post by Some Penguin on 2012-08-03
Honestly, for desktop apps... probably C++, not because it's remotely perfect, but because 

(1) it's old enough, accessible enough, and useful enough to have a massive number of people who know it well,

(2) for the same reasons, it has lots of useful libraries and tools (Qt and GTK come to mind for desktop GUIs, for instance, but history is strewn with many)

(3) it's low-level enough to be highly flexible; if you want to write highly parallel code it's possible; if you need garbage collection there have been numerous memory-management libraries written; practically anything is possible although it may be painful (like dynamically generating methods and adding them to an API... that's something far more easily done in a scripting language)

---

### Post by Mikeb85 on 2012-08-03
Google's Go language maybe?  At least it was created by/has support of the company that will most likely define the tech sector in the future...  Seems to be well thought out. 

I personally am quite fond of Ruby, dunno how fit it is.  It's easy, seems you can get alot done with a very small amount of code.   Edit - oops, Ruby is a scripting language, but still, with bindings to C, C++, Java, etc..., it seems pretty adaptable and likely to be around in the future.  

Keep in mind I'm also a beginner to programming (very, very new - doing it in my spare time for fun), although I know the tech industry fairly well (father was in IT, I invest stocks, tech is one of my favourite sectors).

---

### Post by vexorian on 2012-08-03
HTML5/CSS are not programming languages, but I guess they are *Coding* languages :/

Google's Go currently looks like vaporware. Very little adoption whatsoever and not as much steam as people thought it would have.


No single language will be the one tool for every of the future's problems. No language is that good for every job. In fact, I think that we will see further specialization of languages and less things that are marketted as magic bullets. In the future, I see every language getting more and more LISP-like and C and C++ will not go anywhere.

---

### Post by IReadTheManual on 2012-08-03
C

---

### Post by lisati on 2012-08-03
*cough* [JCL]("http://en.wikipedia.org/wiki/Job_Control_Language") anyone? :D (Just kidding)

---

### Post by bouncingwilf on 2012-08-03
> **lisati said:**
> *cough* [JCL]("http://en.wikipedia.org/wiki/Job_Control_Language") anyone? :D (Just kidding)

AH! those were the days JCL + FORTRAN IV  (and maybe a little bit of PL1 or Cobol)


Bouncingwilf

---

### Post by Simian Man on 2012-08-03
> **Some Penguin said:**
> Honestly, for desktop apps... probably C++, not because it's remotely perfect
Allow me to disagree :).

> **Some Penguin said:**
> 
(1) it's old enough, accessible enough, and useful enough to have a massive number of people who know it well,
There are a fair number of people programming in C++, but very few of them actually know the language well.  Because C++ is so ridiculously complicated, it has some of the least knowledgeable programmers of any language.  Those who are able to make it out are usually elevated to high status in the C++ community.  Besides, there are plenty of languages with enough market-share that beginners can find help, this is a stupid reason to choose a language.

> **Some Penguin said:**
> (2) for the same reasons, it has lots of useful libraries and tools (Qt and GTK come to mind for desktop GUIs, for instance, but history is strewn with many)
This is true, but QT, GTK+ and most other popular libraries have bindings to other languages such as Python.  In fact GTK+ is a C library that has a C++ binding.  It's actually pretty hard to find a popular library nowadays that doesn't have at least a Python binding.  Besides most languages have a foreign function interface that makes communicating with C code pretty easy.

> **Some Penguin said:**
> (3) it's low-level enough to be highly flexible; if you want to write highly parallel code it's possible; if you need garbage collection there have been numerous memory-management libraries written; practically anything is possible although it may be painful (like dynamically generating methods and adding them to an API... that's something far more easily done in a scripting language)
You can write highly parallel code in any modern language, in fact if anything it's harder in C++ due to the fact that threading was only added to the standard library last year and isn't widely supported yet (along with the fact that manual memory management is even trickier in a parallel environment).  And If you need garbage collection, why would you specifically choose one of the only popular languages that doesn't have it built in?  Masochism?

Your argument that "practically anything is possible" makes zero sense.  All reasonable programming languages are Turing-complete, so what can be written in one can be written in another.  Yes you can do a lot with C++, but you can do the same things with Python.  And, as you alluded to, it's often far easier.

There are reasons to pick C++ for a project, such as the small number of times when the performance difference is critical, in embedded or other constrained environments, or when interacting with some legacy application or library.  The reasons you gave, however, are nonsense.


> **IReadTheManual said:**
> C
What a well-articulated response.

---

### Post by DarkAmbient on 2012-08-03
depends on what you wanna do in the future.

C, C++ will most likely stick around for some time. And always be reliable. 

Java is nice both for learning object-oriented programming and writing cross-platform:ish apps.

Just got into python a few weeks ago myself. I think it's a lot easier than the previous two suggestions. Sometimes it looks almost "pseudo-cod:ish" when you write scripts. (I think Python is a script-language though, not a programming one.. might be wrong.. and the difference between the 2 I know nothing about)

Tried a few other languages, but none a much as the (2) ones above. 

I would like some langauge that could do the same as html5 + javascript w/ webgl. Something that perhaps make use of those.. But then.. maybe one could try learn to use html5+javascript+webgl instead...

EOYattering

---

### Post by Simian Man on 2012-08-03
> **DarkAmbient said:**
> Just got into python a few weeks ago myself. I think it's a lot easier than the previous two suggestions. Sometimes it looks almost "pseudo-cod:ish" when you write scripts. (I think Python is a script-language though, not a programming one.. might be wrong.. and the difference between the 2 I know nothing about)

The scripting language vs. programming language thing is largely irrelevant now.  It used to be that programming languages were compiled and used for big projects and scripting languages were interpreted and used for little projects.  That is no longer true for a few reasons.  First computers are fast enough that interpretation is more than fast enough for the majority of uses.  Also the advent of bytecode, JIT compilation and better interpreters has narrowed the gap and blurred the line a bit.

Second, interpreted languages such as Python have many features for large-scale development that were lacking in older "scripting languages" such as objects, exceptions, modules and so on.  You'd have had to be crazy to build a large application in old versions of, for example, Tcl or Perl, but now that is no longer the case, with many large applications written in interpreted languages.

I just refer to all general purpose languages as "programming languages", as the distinction of scripting vs. programming is now largely dead.

---

### Post by trent.josephsen on 2012-08-03
There are a few languages that are really, really good at what they do, to the exclusion of most competitors. C does come to mind; no other language handles the "portable assembly" role quite so well, but it's probably less useful for those not interested in systems programming. Perl, while it faces competition from the likes of Python and Ruby, is still my go-to for small text processing tasks and one-off scripts. Java is great for, umm, I'll get back to you on that one. SQL isn't going anywhere. Nor VHDL.

Point is, there's no best language for "the future"; programmers of the future will use lots of languages, just like we do today. Also C is better than C++. ;)

---

### Post by Debash on 2012-08-03
I'm joining college in a few days and I will be studying C for the first time :)

---

### Post by thek3nger on 2012-08-03
In general every task has its own language. :) My suggestions are:

1) A strong low-level industrial-standard binary language (C/C++ for example)
2) An high level scripting language for quick 'n' easy programming (Python or Lua or Ruby or whatever)
3) Learn how to allow integration between these two languages.

Then I think you can do anything. :D

---

### Post by vexorian on 2012-08-03
C++ is not going away anytime soon. Because coding in C++ is ***freaking cool***. That no one knows more than 75% of it makes it very exciting. C is on the other hand, kind of bland.

True OOP is a lot about templates. Compile-time stuff is something that C++ does very well (perhaps too well). Add in the stuff from c++0x like lambdas and better threads and C++ is going to be a ***complete mess*** to code in and read. This makes it the perfect language to use to learn stuff.

If the language beginners are using is not ultra feature freak and complicated, how are beginners ever going to learn how to program correctly? c++ is a recopilation of all the ways possible to shoot yourself in the foot, and I think that if you don't give beginners the chance to shoot themselves in the foot, they will never get to appreciate the protection from such thing in the higher level languages.

The best thing that can happen to a prospective programmer is to begin programming in a language that will *surely* stab him in the back the first second (s)he turns around. And you can be sure, C++ will. It forges character.

---

### Post by Simian Man on 2012-08-03
> **vexorian said:**
> ...

I can't tell if your post is a joke or complete nonsense.

---

### Post by diesch on 2012-08-03
Canonical seems to usually use Python, Vala, C or C++ for their desktop programs, where C is oft used for libraries.

Python is usually a good choice for desktop programming. Beeing able to understand simple C and C++ code is sometimes needed to understand some docs or examples.

---

### Post by lisati on 2012-08-03
> **bouncingwilf said:**
> AH! those were the days JCL + FORTRAN IV  (and maybe a little bit of PL1 or Cobol)


Bouncingwilf

Back in the day when I first used JCL, I often used a little program called IFOX00, otherwise known as assembler.

---

### Post by vexorian on 2012-08-03
> **Simian Man said:**
> I can't tell if your post is a joke or complete nonsense.
I don't think anyone can find the true joy of programming until (s)he at least codes one mid size C++ project.

---

### Post by zombifier25 on 2012-08-03
> **vexorian said:**
> I don't think anyone can find the true joy of programming until (s)he at least codes one mid size C++ project.

I concur. I'm learning C++ and Python right now.

---

### Post by codemaniac on 2012-08-04
The toughest nut to crack is learning your FIRST programming language .
The rest are just a walk in the park .

C is just fun and sometimes can give you high adrenaline flow with all its pointer acrobatics .

---

### Post by bcschmerker on 2012-08-04
ANSI C, as developed by Bell Laboratories, is the de facto standard cross-architecture programming language, and its C++ derivative is fully supported by the GNU® Compiler Collection; it should be sufficient for not only hardware drivers but also plug-in procedures for access from the scripting languages used at application level.

As a side note, I am currently searching for resources for SQLite, a high-level language for databases derived from ANSI Structured Query Language (as developed for University of California DB2); many recent applications use SQLite for application-specific databases.

---

### Post by dagoth_pie on 2012-08-04
> **vexorian said:**
> I don't think anyone can find the true joy of programming until (s)he at least codes one mid size C++ project.
I agree, C++ is only harder because you have to think about what you're doing.

I'd love to be doing C++ coding at the moment. Just the other day I had one of those rare opportunities where multiple inheritance would have been useful, but unfortunately C# protected me from shooting myself in the foot, so I had to do it the long way.

---

### Post by Some Penguin on 2012-08-04
> **vexorian said:**
> I don't think anyone can find the true joy of programming until (s)he at least codes one mid size C++ project.

Perhaps.  That said, it's also perhaps relatively difficult for e.g. purely reference-based languages to match the sheer rage that can be induced when a single careless programmer responsible for a single library introduces memory corruption in your application by occasionally writing to the wrong memory address, thus providing a fairly subtle and possibly difficult-to-reproduce source of error.      There's something to be said for languages which make it easier to prevent unwanted side-effects from percolating all throughout the system.

---

