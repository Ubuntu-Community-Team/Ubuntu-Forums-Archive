---
title: "Easy Programming Language.."
date: 2008-05-16
forum: Programming Talk
---

### Post by GCoffee on 2008-05-16
Hello,

I am a former windows user and was quite good at Autoit. However, although you can run autoit under wine i would prefer to use a native language.

I have looked at gambas but cannot find a good tutorial for it.

Here are the specifications for the langauge:

Easy to learn
Create's GUI's easily
Functionality

Thats all. 

Thanks,
GCoffee.

---

### Post by Joeb454 on 2008-05-16
You may want to look into Python :) It's a very easy language to learn from what I've heard :)

---

### Post by dashnak on 2008-05-16
Also, you could try lazarus, which is a free implementation of free object pascal and is quite similar to delphi.

---

### Post by LaRoza on 2008-05-16
See the sticky. I wouldn't recommend anything Pascal based though.

---

### Post by GCoffee on 2008-05-16
> **LaRoza said:**
> See the sticky. I wouldn't recommend anything Pascal based though.

Which sticky? Could you give me a link?

---

### Post by LaRoza on 2008-05-16
> **GCoffee said:**
> Which sticky? Could you give me a link?

Thread has been moved, so it is the sticky in this forum.

---

### Post by ivze on 2008-05-16
Se Java with Netbeans IDE. Much info is at [http://java.sun.com/docs/books/tutorial/index.html](http://java.sun.com/docs/books/tutorial/index.html) .
In my opinion, Java is the best for programming applications, that do something useful that is not connected to low-level system activities.

1)The language is designed that there appear less bugs (e.g. no memory management, not allowing to skip many exceptions forcing a programmer to think of them).
2)Cross-platform (well-designed programm will be binary portable to Windows, MACOSX, Solaris(Undoubtedly!) ...)
3)Multithreading and synchronisation is included in language specification -- writing multithread application is easier than in C++ (with pthreads).
4)Very nice networking included in language standarts.
5)only 2-4 times slower than C++ (google java c++ performance)
6)Very good GUI constructor in Netbeans.
7)C++ like beautiful syntax (can't understand those, who like Python =P=))

---

### Post by LaRoza on 2008-05-16
> **ivze said:**
> Se Java with Netbeans IDE. Much info is at [http://java.sun.com/docs/books/tutorial/index.html](http://java.sun.com/docs/books/tutorial/index.html) .
In my opinion, Java is the best for programming applications, that do something useful that is not connected to low-level system activities.


I think Blub is.

The sticky has all the information I think.

---

### Post by MONODA on 2008-05-16
> See the sticky. I wouldn't recommend anything Pascal based though.
why not? is it because they are difficult, my first language was pascal, it was too easy.

---

### Post by LaRoza on 2008-05-16
> **MONODA said:**
> why not? is it because they are difficult, my first language was pascal, it was too easy.

I don't want to get involved in a flamewar here. It is probably easy to learn, but that is not why I recommend against it.

---

### Post by b1g4L on 2008-05-16
I would also recommend Python as a good starter language to learn. The syntax is rather simple to learn. You are exposed to Object Oriented Programming. The REPL(Read Eval Print Loop) is very handy, especially when trying to figure out "What does this code do." There are plenty of tutorials and resources online to learn Python. Good luck.

---

### Post by pmasiar on 2008-05-16
> **ivze said:**
> Java...

ivze, your mind seems to be locked in Java and C++ - are you a blub programmer? There are many more languages beyond those two.

> 1)The language is designed that there appear less bugs ...

Python has also automatic memory management, and also more convenient features missing in Java or planned to be added like generics. Strong typing is pain for beginner, and static type checking is evil pain for beginner and expert. Python wins.

> 2)Cross-platform ...binary portable ...

Binary compatibility in Java adds complexity (classpath anyone) - open source is enough for most usecases. Python wins.

> 3)Multithreading and synchronisation ...

is not easy and needed, but complicates java. Python wins.

> 4)Very nice networking included in language standarts.

Same in Python - draw

> 5)only 2-4 times slower than C++ (google java c++ performance)

Even if code performance is slower (unless you compile the code with psyco or so), **speed of development** is 10 times faster in Python. Python wins.

> 6)Very good GUI constructor in Netbeans.

Python loses - Sun has more money to sink into developing free tools. But many programmers prefer mastering universal editors like vim, Emacs, and use them with all languages. Also, there are Komodo, Eric, SPE and other IDEs for Py. GUI is not the only way: No need of GUI for simple one-off programs, and web apps are also designed differently.

> 7)C++ like beautiful syntax (can't understand those, who like Python =P=))[/QUOTE]

Don't tell your GF that you consider C syntax beautiful :-) Python obviously wins this one

---

### Post by keeler1 on 2008-05-16
the PyDev plugin for eclipse is pretty good.  Just make sure not to download eclipse from the repositories as it uses gcj and is very buggy and slow.

There are also many applications which can output python code for gui stuff.  wxGlade is one that I can think of.  It takes a little while to get used to but it is pretty good.

---

### Post by ivze on 2008-05-16
> **pmasiar said:**
> ivze, your mind seems to be locked in Java and C++ - are you a blub programmer? There are many more languages beyond those two.

> 1)The language is designed that there appear less bugs ...

Python has also automatic memory management, and also more convenient features missing in Java or planned to be added like generics. Strong typing is pain for beginner, and static type checking is evil pain for beginner and expert. Python wins.

> 2)Cross-platform ...binary portable ...

Binary compatibility in Java adds complexity (classpath anyone) - open source is enough for most usecases. Python wins.

> 3)Multithreading and synchronisation ...

is not easy and needed, but complicates java. Python wins.

> 4)Very nice networking included in language standarts.

Same in Python - draw

> 5)only 2-4 times slower than C++ (google java c++ performance)

Even if code performance is slower (unless you compile the code with psyco or so), **speed of development** is 10 times faster in Python. Python wins.

> 6)Very good GUI constructor in Netbeans.

Python loses - Sun has more money to sink into developing free tools. But many programmers prefer mastering universal editors like vim, Emacs, and use them with all languages. Also, there are Komodo, Eric, SPE and other IDEs for Py. GUI is not the only way: No need of GUI for simple one-off programs, and web apps are also designed differently.

> 7)C++ like beautiful syntax (can't understand those, who like Python =P=))

Don't tell your GF that you consider C syntax beautiful :-) Python obviously wins this one[/QUOTE]
I don't say, I dislike Python! 
Python has it's own specific place among the languages.
I understand well, that in certain cases using interpreted, high-level and slow languages is reasonable. I am an Octave/Matlab user, and know how to make such languages work good  -  use modules, written in C++/Fortran, to make calculations. Programming physical simulations by the means of using ready modules (e.g. sparse matrix solver) in Octave/Matlab is much better than writing the main programm in one of those (C++/F) languages.
Moreover, I understand the conception of glue-language; python makes the job of such a language well.

To conclude, I must say, that which language to choose strongly depends on the person's programming needs. Neither java, nor Python can do everything. Only assembler can!(:P)

---

### Post by LaRoza on 2008-05-16
> **keeler1 said:**
> 
There are also many applications which can output python code for gui stuff.  wxGlade is one that I can think of.  It takes a little while to get used to but it is pretty good.

The sticky has links for such apps, as does my wiki.

---

### Post by pmasiar on 2008-05-16
> **ivze said:**
> Neither java, nor Python can do everything. Only assembler can!(:P)

You seems to confuse 'possibility' and 'feasibility'. Yes, everything is possible in ASM (or C, there is hardly any difference). You are aware about [Turing completeness](en.wikipedia.org/wiki/Turing_completeness) of most programming languages?

But most tasks are not feasible to do in ASM - too hard to do. This is exactly why we have higher level languages: to make more complex tasks **feasible**.

Read [Humble Programmer](http://www.cs.utexas.edu/~EWD/transcriptions/EWD03xx/EWD340.html) and [The Hundred Year language](http://www.paulgraham.com/hundred.html) and be enlightened :-)

---

### Post by durand on 2008-05-16
I've just started learning Python and I would highly recommend it. It's really simple to understand and learn and its also very powerful. The only problems I've been having so far is knowing what to use in a situation but the internet helps :).
If you do choose python, you should take a look at SPE. Its a really good editor for python. (look at my sig)

---

### Post by slavik on 2008-05-16
> **pmasiar said:**
> You seems to confuse 'possibility' and 'feasibility'. Yes, everything is possible in ASM (or C, there is hardly any difference). You are aware about [Turing completeness](en.wikipedia.org/wiki/Turing_completeness) of most programming languages?

But most tasks are not feasible to do in ASM - too hard to do. This is exactly why we have higher level languages: to make more complex tasks **feasible**.

Read [Humble Programmer](http://www.cs.utexas.edu/~EWD/transcriptions/EWD03xx/EWD340.html) and [The Hundred Year language](http://www.paulgraham.com/hundred.html) and be enlightened :-)

"too hard to do" does mean that the task is not feasible. "Not feasible" means "impossible." and if something is impossible in one language and possible in another, they are not Turing equivalent.

brainfuck is a Turing complete language (as the wikipedia entry you link to) shows. Therefore, it can do anything that any other Turing complete language can.

Turing completeness does not say anything about complexity, only about computability. Selection (Linear) sort is equivalent to Heap sort even though the complexity is different.

---

### Post by pmasiar on 2008-05-17
> **slavik said:**
> "too hard to do" does mean that the task is not feasible. "Not feasible" means "impossible."

'possible' and 'feasible' are almost synonyms, but 'feasible' means also 'practical'. Something what is possible in theory might be not feasible is ie it takes centuries to complete.

Unless you are god, of course - then you have all the time. :-)

> and if something is impossible in one language and possible in another, they are not Turing equivalent.

I agree, but I was talking about feasibility, not possibility. Most languages are Turing equivalent, but it does not tell us anything about feasibility to solve certain kind of problem in a given language, with given limits. Software is engineering, it is about balancing requirements, cutting corners where you can, and focusing on what is important.

---

### Post by slavik on 2008-05-17
> **pmasiar said:**
> 'possible' and 'feasible' are almost synonyms, but 'feasible' means also 'practical'. Something what is possible in theory might be not feasible is ie it takes centuries to complete.

Unless you are god, of course - then you have all the time. :-)

> and if something is impossible in one language and possible in another, they are not Turing equivalent.

I agree, but I was talking about feasibility, not possibility. Most languages are Turing equivalent, but it does not tell us anything about feasibility to solve certain kind of problem in a given language, with given limits. Software is engineering, it is about balancing requirements, cutting corners where you can, and focusing on what is important.
[http://en.wiktionary.org/wiki/feasible](http://en.wiktionary.org/wiki/feasible)

feasible = possible; capable of being done.

There is a very famous quote by Larry Wall in the Camel book. "Perl makes easy things easier, difficult things not impossible."

You either want to talk ebout complexity or computability. I think you are confused about which of these 2 concepts you are talking about, since you argue about complexity (how difficult is something to do) by referencing Alan Turing (who spoke about computability).

Turing equivalency does not talk about complexity at all, it is simply not an issue, computability is. Brainfuck is turing equivalent to C, that's it, end of story. It doesn't matter how long it takes to solve a problem using brainfuck, the fact is that it is still Turing equivalent to C.

One item that the Turing machine and Turing equivalency take into account is 'infinite time.'

---

### Post by rickh57 on 2008-05-17
I'm a software engineer, using many different languages, but from looking at what's out there, I agree with the suggestion to start with Python. It is powerful, but simple to get started with.

---

### Post by slavik on 2008-05-17
> **rickh57 said:**
> It is powerful, but simple to get started with.

I could say the same about many languages ...

---

### Post by rlameiro on 2008-05-17
Well I also think that Python is easy to start to. I am a hobby programmer and after advices from people here in the forum (roza and others, Thankxs :) ) I started to learn python. For now I can't do much, I dont have so much time and mental freshness to move faster, but in the same time with C I couldn't do the same... even knowing some assembly. Another thing very important is that you have plenty of information on the internet (so much that you can be lost :) ), very good libraries and suport to GUIs (Tkinter, Qt, GTK, WxWidgets, etc.). I even buyed a book (in portuguese my native language, nothing replaces a good hardcopy to read at :) ).
Well it is only my 1,5 cents...
P.S. Good luck for the programming :)

---

### Post by pmasiar on 2008-05-17
> **slavik said:**
> Brainfuck is turing equivalent to C, that's it, end of story. It doesn't matter how long it takes to solve a problem using brainfuck, the fact is that it is still Turing equivalent to C.

One item that the Turing machine and Turing equivalency take into account is 'infinite time.'

Now I know why you love Perl. :-)

I am pragmatic programmer, for me it **does** matter how long it will take me to have a solution. It is one of main criteria.

"In theory, there is no difference between theory and practice. In practice, there is" :-)

---

### Post by slavik on 2008-05-17
> **pmasiar said:**
> Now I know why you love Perl. :-)

I am pragmatic programmer, for me it **does** matter how long it will take me to have a solution. It is one of main criteria.

"In theory, there is no difference between theory and practice. In practice, there is" :-)
What does Turing equivalence have to do with how long it takes to have a solution?

It took me about 6 hours (on and off) to write a 9 by 9 sudoku solver in C. In prolog it would take about 30minutes (at most).

---

### Post by pmasiar on 2008-05-18
> **slavik said:**
> What does Turing equivalence have to do with how long it takes to have a solution?

It is not **feasible** to have meaningfull discussion with someone trying hard NOT understand. See you in another thread.

---

