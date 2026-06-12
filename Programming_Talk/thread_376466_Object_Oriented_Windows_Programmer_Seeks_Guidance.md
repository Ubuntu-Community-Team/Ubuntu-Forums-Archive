---
title: "Object Oriented Windows Programmer Seeks Guidance"
date: 2007-03-04
forum: Programming Talk
---

### Post by JugglesGeese on 2007-03-04
Hi all...

By trade, I'm a .Net programmer under windows.  My day job is development and testing of web and windows applications using VB and C#. I like to think that I'm semi well versed in fairly advanced OO techniques such as code separation and design patterns.  However, all my time is spent in the trenches of business logic and database programming.  Every application I develop seems to gravitate towards the same model:

[LIST]
[*]UI
[*]Presentation
[*]Business Logic
[*]Database Manipulation Code
[*]Data store
[/LIST]

I'd like to learn more about programming applications that do not rely on the database model.  I'm more interested in system I/O and manipulating file types, specifically audio and video.  One project that I have in mind is programming against my video iPod   I know there are already a ton of projects out there that I could already use as a template.  However, I'd like to begin my learning process with a language I'm already familiar with.  Since I'm coming from windows, that narrows my choices to Java and, well, Java. 

I guess I've become pretty lazy and complacent while using windows, because every application I ever wanted existed.  Now, in linux, I find myself having to fend for myself, and I'd really like to be more self sufficient under linux rather than go crawling back to Micro$oft Window$. So, any resources that anyone could point me in the direction of for my quest would be helpful.

Thanks!

---

### Post by bukwirm on 2007-03-04
If you are interested in lower-level programming, C and C++ are essential. Searching the forums and Google should turn up lots of information and other resources.

---

### Post by pmasiar on 2007-03-04
> **JugglesGeese said:**
> By trade, I'm a .Net programmer under windows.  My day job is development and testing of web and windows applications using VB and C#. (...)
I'd like to learn more about programming applications that do not rely on the database model.  I'm more interested in system I/O and manipulating file types, specifically audio and video.  One project that I have in mind is programming against my video iPod   I know there are already a ton of projects out there that I could already use as a template.  However, I'd like to begin my learning process with a language I'm already familiar with.  Since I'm coming from windows, that narrows my choices to Java and, well, Java. 

Java reinvented everything to make its own platform, and does not play nicely with C libraries which are fundamentals of Linux. Most projects you will find will be IMHO in C/C++. It should not be too hard to pick up, compared to java. Only big difference will be getting used to proper memory management - no garbage collection... Check couple projects which you like, maybe post couple questions to developers, and dive right in!

---

### Post by Tuna-Fish on 2007-03-05
Also, learn at least a single scripting language. C# and Java are kind of intermediate languages, between scripts and "proper" languages. In windows world, everything is usually done with such intermediate languages, in Linux, the work is split between scripts, which are very quick and easy to write and maintain, but are slow to execute, and C/C++ which compiles to machine code and is thus very quick to execute but is hard and slow to write and maintain.

Thus, the first thing to do when coding something in Linux is to identify which parts of the software need to be 'fast' and which can be 'slow'. If you're lucky, the entire program can be slow and be written in some scripting language, making it a lot faster and easier to code. It is a common paradigm to write everything you possibly can in a script, as scripts are naturally portable and both have less bugs and are easier to debug.

Probably the best scripting language to start with is python, as it is really quite similar to Java except it is slightly slower and has a lot better standard library. I was trained in Java and with the help of my Java experience picked up most of python in 2 days, so it's not hard to learn.

---

### Post by pmasiar on 2007-03-05
> **Tuna-Fish said:**
> Thus, the first thing to do when coding something in Linux is to identify which parts of the software need to be 'fast' and which can be 'slow'. If you're lucky, the entire program can be slow and be written in some scripting language, making it a lot faster and easier to code. It is a common paradigm to write everything you possibly can in a script, as scripts are naturally portable and both have less bugs and are easier to debug.

I agree with Tuna-Fish: learning scripting language like Python will open your mind for new levels of productivity. It is also called rapid prototyping language. Or "executable pseudocode" :-)

But sometimes is not easy to guess which parts of program will be slow. Simpler mthod is to create pilot draft implementation quickly in scripting language, figure out application structure, control flows etc. Then you can profile which parts of program are taking 80% of the time and rewrite those in C - which is easy to link to Python code. 

Zen of Python: "In face of ambiguity, refuse temptation to guess".

Do not guess where the bottleneck is - measure it.

---

### Post by JugglesGeese on 2007-03-05
Thanks for all your input.  

From what you all say, I should pick up a scripting language like python first and get comfortable with it.  Then, once I have that down, I should dive into c or c++.  I guess I sort of learned things backwards.  I got into programming as a side interest at my last job.  I picked up server-side web scripting first, then moved into .net, then java, so my learning curve for c is pretty steep.  I believe it's always easier to start with the lower level languages and move into the higher level stuff, but I'm going the opposite direction 

Any good python tutorials that you all want to pass along?

---

### Post by pmasiar on 2007-03-05
> **JugglesGeese said:**
> 
From what you all say, I should pick up a scripting language like python first and get comfortable with it.  Then, once I have that down, I should dive into c or c++. 

good plan

> I picked up server-side web scripting first, then moved into .net, then java, so my learning curve for c is pretty steep.  I believe it's always easier to start with the lower level languages and move into the higher level stuff, but I'm going the opposite direction 

Different languages have different obstacles to learn.

low-level languages like assembler are very hard - you have to control everything. Layer above is C. it is simpler than Assembler, but simpler than java/ C++ too: in C, no sane person would create complicated object hierarchies in C, IMHO.

Python is rather special: is OO as Java/C++ if you need it, but if not, it is simpler than C because takes care for all type information for you, dynamically. You should be able to pick Python in a week, easy.

I have wiki for Python beginners, including online books: [http://learnpydia.pbwiki.com/HowToStart](http://learnpydia.pbwiki.com/HowToStart) . Good online book for experienced programmer is "Thinking as conputer scientist", google knows where.

---

### Post by hscottyh on 2007-03-05
I'm a c# business programmer as well. That seems to mostly the model my programs tend to be as well.

I'm having fun at home playing with c# under mono. It's pretty freakin impressive to see a GUI exe you wrote in Visual Studio 2003 run just fine under linux. 

I'm trying to get my head around gtk#, so I can write native gnome gui's.

---

### Post by JimmyBEng on 2007-03-05
try this thread that has been stickied.

[ How to start programming - guides and links for many languages]("http://www.ubuntuforums.org/showthread.php?t=333867")

It lists resources for both python and C++  (as suggested above) and other stuff too.

---

