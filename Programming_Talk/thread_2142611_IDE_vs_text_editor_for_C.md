---
title: "IDE vs text editor for C"
date: 2013-05-06
forum: Programming Talk
---

### Post by lordfkiller on 2013-05-06
This a very old controversial topic. I did google it, but still I'd like to know people's ideas here.

Do you prefer IDE or text editor + command line for C programming? I know that I definitely prefer an IDE for Java. The programs are big and things like the refactoring features are really needed. But I also see that many people do not use IDEs for languages like C.

Whether you prefer IDE or text editor, please give your reasons.

Thanks!

---

### Post by MG&amp;TL on 2013-05-06
A text editor. Personally I find being able to manipulate text fast considerably more advantageous than an IDE (for some reason, I've yet to see an IDE with a decent editor - Qt Creator's FakeVim is okay, but most of the features are missing), and I don't really use the IDE features like refactoring. 

Personally, *vim*, *make* and *NERDTree* are all I need for C programming.

---

### Post by trent.josephsen on 2013-05-06
> **MG&TL said:**
> Personally I find being able to manipulate text fast considerably more advantageous than an IDE (for some reason, I've yet to see an IDE with a decent editor[...])

This, pretty much. I've used several IDEs, Eclipse and Netbeans probably the most, and the editors are just not up to par. They all do broken things when typing long lines, or don't support the indent style you prefer (or policy dictates you use), or are fundamentally broken in some other way that no dedicated editor is. And you can just forget about "advanced" features like macros, multiple selection buffers, and calling external programs to manipulate your text. Of course, nothing prevents you (in theory) from doing your editing in some other program and using the IDE for everything else.

Also, maybe it's just me, but I find the idea of "refactoring" kind of odd and slightly bandwagonish, especially with Java. C programmers will "clean up" or "restructure" or even just "change" code, once in a while because style or new features demand it, but it seems like Java guys spend half their time "refactoring" code. Not that refactoring is never needed, but if you find yourself doing it all the time to the same codebase, maybe that means it's time to step away from the editor and do some actual design, which will probably save time in the long run. Maybe it's because Java is sometimes used to mitigate the damage that poor coders can do to important projects, which is the same kind of environment I imagine automated refactoring would be most useful.

There's definitely an aspect of size, too -- bigger projects benefit more from browseable code hierarchies and such things that are difficult-to-impossible or just take a long time to set up in a general purpose editor. None of the projects I have worked on were big enough that I thought an IDE was needed. Sometimes, too, it helps to have everybody who works on a project on the same page as far as tools go -- which is easy to do if everybody uses the exact same software. But my personal preference is to use an editor and invoke the compiler or interpreter from a command line.

---

### Post by King Dude on 2013-05-07
For the C family programming language? An IDE is what I recommend.

My favorite IDE is Code::Blocks. I recommend it to everyone interested in programming in C/C++.
[http://www.codeblocks.org/](http://www.codeblocks.org/)

---

### Post by Bresser on 2013-05-07
I find a IDE a lot easier at least for c/c++. I have used Code:Blocks and Netbeans and both are great. Both offer Qt which is extremely beneficial.

---

### Post by rnerwein on 2013-05-07
> **lordfkiller said:**
> This a very old controversial topic. I did google it, but still I'd like to know people's ideas here.

Do you prefer IDE or text editor + command line for C programming? I know that I definitely prefer an IDE for Java. The programs are big and things like the refactoring features are really needed. But I also see that many people do not use IDEs for languages like C.

Whether you prefer IDE or text editor, please give your reasons.

Thanks!
hi
i am using "vi" and "ctags" since about 30 years. why - that stuff is available even on "hosts !". i never worked on a system where there was'nt a vi available.
;-)
ciao

---

