---
title: "Best programming language to start with?"
date: 2008-05-16
forum: Programming Talk
---

### Post by linkmaster03 on 2008-05-16
What would be a good programming language to start with that is text in the terminal, but can have simple GUIs?

Where might I find a tutorial to learn said language?

---

### Post by Falcorian on 2008-05-16
I'm a big fan of python, I write all my scripts in it now.

It has [Dive Into Python](http://www.diveintopython.org/) which is pretty good.

---

### Post by CloudFX on 2008-05-16
Have a look at the Documentation Page about programming: [https://help.ubuntu.com/8.04/programming/C/index.html](https://help.ubuntu.com/8.04/programming/C/index.html)

---

### Post by PinkFloyd102489 on 2008-05-16
Writing bash scripts are fairly simple and can help you automate things on your computer.

---

### Post by Mr A Mouse on 2008-05-16
The important thing to learn (imo) is the actual art of programming itself, which transcends specific languages. 

That being said, the question of "best programming language" can only be answered by asking you "What do you want to learn?" There are compiled languages, scripting languages, general purpose languages, specialized languages ... the list goes on, and there is no single "best" language to learn programming in.

[O'Reilly]("http://radar.oreilly.com/archives/2008/03/state-of-the-computer-book-mar-23.html") has some interesting trend information based on book sales. Java is still the leading individual language in the world market, but is falling while C# (in second) is gaining more market share. C/C++ hold about 9% of the market, but most of the core programming on Linux systems is done in C, with C++ coming in second, IIRC. They're all good-- but the most important question (and the onle that only you can answer) is what will be best for *you?*

---

### Post by Joeb454 on 2008-05-16
Take a look at the sticky in Programming Talk (it's in the Development Forum).

Personally I think python is the easiest to start with

---

### Post by LaRoza on 2008-05-16
> **linkmaster03 said:**
> What would be a good programming language to start with that is text in the terminal, but can have simple GUIs?

Where might I find a tutorial to learn said language?

Many, but I would recommend Python + EasyGUI. See my wiki.

Thread moved.

---

### Post by Wybiral on 2008-05-16
The best language to start with is English, because you can use it to read stickies and search the forum.

---

### Post by slavik on 2008-05-16
> **Wybiral said:**
> The best language to start with is English, because you can use it to read stickies and search the forum.

QFT

---

### Post by days_of_ruin on 2008-05-16
> **Falcorian said:**
> I'm a big fan of python, I write all my scripts in it now.

It has [Dive Into Python](http://www.diveintopython.org/) which is pretty good.

Dive into Python is not a beginner book!Google "a byte of python".

---

### Post by mikazo on 2008-05-16
My first year in computer science dealt with C and Java, both of which can be developed and run using the terminal. I found that I learned a lot from C to do with memory management and pointers, and I learned a lot from Java regarding GUIs and user interfaces, as well as the concept of object-oriented programming.

---

### Post by LaRoza on 2008-05-16
> **days_of_ruin said:**
> Dive into Python is not a beginner book!Google "a byte of python".

Why google when all that work has been done and recorded in wikis and the stickies?

---

### Post by Sinkingships7 on 2008-05-16
> **Wybiral said:**
> The best language to start with is English, because you can use it to read stickies and search the forum.

I laughed *very* hard.  :lolflag:

---

### Post by pmasiar on 2008-05-17
> **Mr A Mouse said:**
> 
[O'Reilly]("http://radar.oreilly.com/archives/2008/03/state-of-the-computer-book-mar-23.html") has some interesting trend information based on book sales.

Agree, with some comments: Java is so huge and complicated that there is whole industry of java books, and suckers (like me) who have to buy and read it. Big part of that byzantine complexity is static typing and childlike obsession with defining classes. Say, why Python can live with one file-like type (with attributes passed when opening file if it is input, output, binary, text, etc), while java has more than 60 file-related types?

Because Python is much simpler in design, it requires less books to master - and there are many free online books, which are below O'Reilly's radar and making Python less popular from POV of a book publisher - but POV of a software developer might be different.

Of course Python can use more book, and they will come, and I love O'Reilly's books. Just understand that O'Reilly trends have bias, too, like anyone else.

---

### Post by slavik on 2008-05-17
> **pmasiar said:**
> Agree, with some comments: Java is so huge and complicated that there is whole industry of java books, and suckers (like me) who have to buy and read it. Big part of that byzantine complexity is static typing and childlike obsession with defining classes. Say, why Python can live with one file-like type (with attributes passed when opening file if it is input, output, binary, text, etc), while java has more than 60 file-related types?

Because Python is much simpler in design, it requires less books to master - and there are many free online books, which are below O'Reilly's radar and making Python less popular from POV of a book publisher - but POV of a software developer might be different.

Of course Python can use more book, and they will come, and I love O'Reilly's books. Just understand that O'Reilly trends have bias, too, like anyone else.

Are you making the case against Java the language or Java the library?

---

### Post by CptPicard on 2008-05-17
> **slavik said:**
> Are you making the case against Java the language or Java the library?

I believe he is making the case that Java the language causes the explosion of types in Java the library/libraries. I have to agree with him, fighting the type system is 50% of work with Java.

---

### Post by slavik on 2008-05-17
> **CptPicard said:**
> I believe he is making the case that Java the language causes the explosion of types in Java the library/libraries. I have to agree with him, fighting the type system is 50% of work with Java.
That is why I like Perl. :)

3 types, that's it.

---

### Post by LaRoza on 2008-05-17
> **slavik said:**
> 
3 types, that's it.

I like Brainfuck. One type, and that is it.

---

### Post by neorou on 2008-05-17
> **linkmaster03 said:**
> What would be a good programming language to start with that is text in the terminal, but can have simple GUIs?

Where might I find a tutorial to learn said language?

Linkmaster,
I would try Python first. Here is a good beginners' tutorial: [http://hetland.org/writing/instant-hacking.html](http://hetland.org/writing/instant-hacking.html)

It has IDLE (on your ubuntu pc, open up your terminal and type Python), which is the interpreter that comes with almost every distribution of Python. You can follow the tutorial above and see if it at least interests you. 

If you like Magnus' tutorial, get his Apress book:
[http://hetland.org/writing/beginning-python/](http://hetland.org/writing/beginning-python/)

I have it and it has helped me a lot. It is not as easy as most people make it sound. You can use Python in almost every programming environment.

Best of luck.

---

### Post by pmasiar on 2008-05-17
> **slavik said:**
> Are you making the case against Java the language or Java the library?


Both :-) but mostly the library.

We could start "why I love/hate Java" thread and link it from FAQ: [http://ubuntuforums.org/showthread.php?p=4716120](http://ubuntuforums.org/showthread.php?p=4716120)

In language itself, I hate the pattern ```
VeryLongTypeName longType = new VeryLongTypeName();
```

I think that Java could use assignment with casting to the type of left side, using say := for that. And of course library is **known** to be byzantian. :-)

---

### Post by slavik on 2008-05-17
> **pmasiar said:**
> Both :-) but mostly the library.

We could start "why I love/hate Java" thread and link it from FAQ: [http://ubuntuforums.org/showthread.php?p=4716120](http://ubuntuforums.org/showthread.php?p=4716120)

In language itself, I hate the pattern ```
VeryLongTypeName longType = new VeryLongTypeName();
```

I think that Java could use assignment with casting to the type of left side, using say := for that. And of course library is **known** to be byzantian. :-)

While I do not like the pattern, this does force explicit creation of references. Remember the probe that NASA lost that was programmed in FORTRAN.

---

### Post by Wybiral on 2008-05-17
> **LaRoza said:**
> I like Brainfuck. One type, and that is it.

It's more readable than Perl too!

---

### Post by slavik on 2008-05-17
I have to agree. :(

Not only that, brainfuck has only 8 operations!!!

---

### Post by LaRoza on 2008-05-17
> **Wybiral said:**
> It's more readable than Perl too!

Brainfuck is very easy to read. It isn't that easy to write, but reading it is simple (left to right, whitespace doesn't matter, and [] are loops)

---

### Post by LaRoza on 2008-05-17
> **pmasiar said:**
> 
We could start "why I love/hate Java" thread and link it from FAQ: [http://ubuntuforums.org/showthread.php?p=4716120](http://ubuntuforums.org/showthread.php?p=4716120)


I was trying to see if I could make it out of this thread, but I couldn't find a suitable first post for it.

If someone wants to make a thread defending/attacking Java, I will add the link. I was going to make it myself...but I didn't.

---

