---
title: "What language to learn?"
date: 2007-08-08
forum: Programming Talk
---

### Post by mevets on 2007-08-08
I am unsure of what programming language I should learn. I am an 18 year old just about to enter college. I know a little PHP and MySQL, but am certainly not a pro. I've worked on 3 small projects that I'm proud of. I also know AHK, which is a open source macro writing language for Windows. It's really an undiscovered gem. AHK is really where I got my start and is the language I know the most completely. I also know some VB.NET because junior year it was taught in one of my classes. I was really impressed with VB.NET and started on it even more after that class ended, but stopped using it because I did not want to be tied to one platform.

Now, I want to move on. Idealy, I want to learn a cross-platform language meant for the desktop. PHP is great but I care more about the desktop than the server. I looked into Python mainly because I heard Ubuntu did a lot of new development in it. All the IDEs for python in the Ubuntu repos seemed really old. Is python an obselete language? I also looked in Mono because of its compatability with VB.NET. I tried to open a VB.NET project but couldnt get it to work. Could anyone tell me how? Cause I think Mono and MonoDevelop might be a good choice for mme considering my past experience with VB.NET.

Anyway what would everyone suggest I learn?

---

### Post by mssever on 2007-08-08
> **mevets said:**
> Idealy, I want to learn a cross-platform language meant for the desktop. PHP is great but I care more about the desktop than the server. I looked into Python mainly because I heard Ubuntu did a lot of new development in it. All the IDEs for python in the Ubuntu repos seemed really old. Is python an obselete language? I also looked in Mono because of its compatability with VB.NET. I tried to open a VB.NET project but couldnt get it to work. Could anyone tell me how? Cause I think Mono and MonoDevelop might be a good choice for mme considering my past experience with VB.NET.

Anyway what would everyone suggest I learn?

Python certainly isn't obsolete. Part of the problem is that a lot of Python stuff is written using the Tk GUI toolkit, which I consider obsolete. But Python itself works well with GTK (PyGTK) and wxWidgets (wxPython). And don't judge a language too much by IDEs. A great many Linux programmers don't use IDEs, preferring text editors such as vim or emacs instead. And since most Linux programs are written to scratch an itch, there really isn't a lot in the way of IDEs because there isn't a lot of perceived need.

Ruby is a language that I'm planning to learn when I have time. It seems to me to be a best of all worlds language (at least for an interpreted language). Don't overlook Python, either. many people love it. Personally, I end up frustrated every time I try Python, but that's probably just me.

If you're looking to learn a compiled language, rather than an interpreted one, don't miss C and C++. They're ubiquitous.

Then, of course, there's Java, which is a cross-platform language that tries its hardest to make you type as much as possible due to its annoying verbosity. It's a compiled language that requires an interpreter, so it's kind of the worst of both worlds in that way.

---

### Post by tseliot on 2007-08-08
> **mevets said:**
> Now, I want to move on. Idealy, I want to learn a cross-platform language meant for the desktop. PHP is great but I care more about the desktop than the server. I looked into Python mainly because I heard Ubuntu did a lot of new development in it.
Python is good for the desktop (of course it depends on what you're planning to do)

> **mevets said:**
> All the IDEs for python in the Ubuntu repos seemed really old. Is python an obselete language?
Try eric3 and geany (or SPE from SVN)

---

### Post by Wybiral on 2007-08-08
My vote's on C, C++, or Python.

Better yet, all three! (obviously not at once)

---

### Post by mevets on 2007-08-08
Thanks guys. Surprised to see no one comment on Mono. Anyway though, I think I'm going to be looking furthur C++, Mono, and Python.

More advice welcome!

---

### Post by LaRoza on 2007-08-08
[My wiki]("http://laroza.pbwiki.com")

(Link also in sig)

Any feedback welcome!

---

### Post by pmasiar on 2007-08-08
Which language? It depends what do you want to code. If you want to participate in some open source project, learn that language. 

But I would strongly suggest to start with Python. You can use it for 80% of what you ever will need, from simple text file massaging and web site to numerical processing (using C libraries for heavy lifting) like numPy and RPy.

After mastering Python, you may want to learn C to cover most of remaining 20% (linux kernel, drivers and stuff). 

> **mevets said:**
> Is python an obselete language? 

Definitely not. [Paul Graham](http://en.wikipedia.org/wiki/Paul_Graham), rather smart programmer (and rich venture capitalist, with [smart friends](http://en.wikipedia.org/wiki/Robert_Tappan_Morris))  argues that Python-like language will be here  [100 years from now](http://www.paulgraham.com/hundred.html)

> I also looked in Mono because of its compatability with VB.NET. I tried to open a VB.NET project but couldnt get it to work. 

Slight but annoying differences - this is exactly the reason why many hackers shun Mono. To make it right, you not only need to recode all correct features, but also all bugs and warts. And then you *still* don't have competitive advantage, and MSFT *still* can "innovate" and change APIs, and you can start again. The only way to get cross-platform compatibility is to have non-proprietary open standard, which anyone is free to reimplement. Python is such standard, and it *is* being reimplemented to run also inside .NET and  in JVM (in addition to already implemented cross-platform Python based on free C libraries).

Wiki in my sig has many links to free books, guides, training tasks.

---

### Post by cprofitt on 2007-08-08
I think Mono only makes use of C# on the Linux side...

I learned VB.Net, C# and am now going to do Python. Then it will be C, C++ or Java.

---

### Post by Note360 on 2007-08-08
C# is nice actually, but Java kind of fills that need. Mono is a very controversial subject though.

---

### Post by slavik on 2007-08-09
my take on .NET vs Java

.NET
- a standard, pushed by a big company Microsoft
- the creator only worries about their platform, Windows
- Mono is worked on by Novell

Java
- a standard, pushed by a big company Sun
- has made a vm for linux, windows, solaris, multiple cpu architectures, too.
- creator has CPUs that speed up Java execution greatly (if you really need it), and Sparc is a good architecture (better than x86)

IMO, Java is better for the same reason why Linus likes the new scheduler. The maintainer is more involved in the project.

---

### Post by Dark Star on 2007-08-09
> **Wybiral said:**
> My vote's on C, C++, or Python.

Better yet, all three! (obviously not at once)
2'nd that . C/ C++ clear your basic then head towards higher level ;):guitar:

---

### Post by vexorian on 2007-08-09
.NET is the worst thing you could do if you want a cross platform language.

I hate Java with a passion but heck if they really make it GPL I will push it to death.

Also.

You are young, you got time. Don't learn a language that's a terrible mistake, instead learn programming, don't ever focus on a single language, also try joining some programming competitions those will really get you into this stuff..

--
For "cross platform language for the desktop" either C++ or Java would work, although if used correctly, C++ will integrate with the desktop much better than Java, that said it is a  good starting language if you plan to do much more than just make apps easily, since it will then make you understand plenty of things that will be good to know even if you later decide to use some other languages.

If you just want a quickie and just get into releasing apps and not really learning much then there's python

---

### Post by pmasiar on 2007-08-09
the "one laptop per child" project makes GUI in Python, and they even have slower CPU than most laptops. You don't *have* to do GUI in C++/Java unless you want. Current obsession with statically typed languages has no valid base and will pass within your career duration ... :-) 

More important is to get ready for multicore CPUs and parallell programming IMHO.

---

### Post by vexorian on 2007-08-09
Most importantly, don't fall in unrealistic projections from language fans.

Sugar is a GTK wrap to python, not a GUI coded in python...

---

### Post by LaRoza on 2007-08-09
> **vexorian said:**
> Most importantly, don't fall in fantasticized opinions from language fans.

There are very few languages NOT worth knowing. The only certain thing is you have to start *somewhere*. Python happens to be a rather easier language for a beginner to learn programming basics.

---

### Post by steve.horsley on 2007-08-09
I'll throw my hat in with the rest - Python first because it's easy to learn and understand and you can get to be doing useful things very quickly. (I haven't looked at Ruby, but have heard good things about that too).

Then IMHO, java for larger projects where you need better speed / reliability / compartmentalisation / multithreading and C++ for low-level systems programming.

---

### Post by slavik on 2007-08-09
> **pmasiar said:**
> the "one laptop per child" project makes GUI in Python, and they even have slower CPU than most laptops. You don't *have* to do GUI in C++/Java unless you want. Current obsession with statically typed languages has no valid base and will pass within your career duration ... :-) 

More important is to get ready for multicore CPUs and parallell programming IMHO.
there is a reason that most air traffic software is written in Ada ... it is eve more type strict than C. Also, nasa lost a probe which was coded using a dynamically typed language (don't remember if it was Lisp or something else, but the idea was that someone mispelled a variable in a while loop)

---

### Post by likpok on 2007-08-09
One other language you probably want to learn (especially if you stick with linux) is bash.

Just get to know stuff like loops and command line tools like cat or sed.

While you won't write any big projects with it, it can very helpful when dealing with your system.

But beyond that, you should probably aim to learn a little bit of each "class" of language. That is, learn some C/C++ (or another object-oriented language), learn a scripting language like python or ruby and learn a functional language like Lisp or Haskell. 

Languages are tools. The more types of tools you have in your box, the more classes of problems you  can tackle. To a degree, each tool will aid the others. I remember a story a family friend told me, where he was writing a graphics program in C. The task was made much easier, however, by the fact that he also knew Lisp. Not because actually used Lisp at all, he just had the framework for dealing with a certain type of problem in his head (specifically list processing).

 I second the person you suggested you learn "programming" as opposed to a "language". Ten years ago (more?), there was a saying that, "In ten years, we won't know what the programming language will be, but it will be called Fortran". Now, except for a small subset of tasks, Fortran has fallen to the wayside. Languages come and go.

---

### Post by pmasiar on 2007-08-09
> **slavik said:**
> there is a reason that most air traffic software is written in Ada ... 
... is that US government made that decision years ago. Not sure how is relevant to most people who don't code mission-critical apps for government. Better than COBOL tho :-)

> nasa lost a probe which was coded using a dynamically typed language (don't remember if it was Lisp or something else, but the idea was that someone mispelled a variable in a while loop)

(funny that you misspelled the word "mispelled" :-) )

Strong typing check done by compiler is better than no unit testing at all, but good unit testing uncovers far more errors  than if you just rely on strong compilation check alone.

---

### Post by bribaetz on 2007-08-09
are you new read my wiki page batch tutorial and support site they all could help if your new python or even bash could help if your an older programmer try 
C C++ java
try all the links in my signature

---

### Post by slavik on 2007-08-09
> **pmasiar said:**
> ... is that US government made that decision years ago. Not sure how is relevant to most people who don't code mission-critical apps for government. Better than COBOL tho :-)

> nasa lost a probe which was coded using a dynamically typed language (don't remember if it was Lisp or something else, but the idea was that someone mispelled a variable in a while loop)

(funny that you misspelled the word "mispelled" :-) )

Strong typing check done by compiler is better than no unit testing at all, but good unit testing uncovers far more errors  than if you just rely on strong compilation check alone.
dude, I swear to god there were two s's there ... the php forums software hates me and dropped one :P

---

