---
title: "Best language to learn how to program"
date: 2007-01-18
forum: Programming Talk
---

### Post by jae1227 on 2007-01-18
What is best language to learn how to program. I first started with trying Java. Then I felt that it was too hard. So then I began working to learn Python. It has been easy to understand. Then I heard  the C++ is the best language to learn. I think that i will stick with Python.

---

### Post by Tomosaur on 2007-01-18
I think you just answered your own question. Whichever you like best. Python may not prepare you very well for other languages though, it may be TOO easy and clean.

---

### Post by Mirrorball on 2007-01-18
My advice is: start with Python, learn C/C++, then Assembly. But it's more important to learn the basics of programming that are not language-especific: algorithms, data structures, object-oriented design, how to test and debug your programs, how to write programs that are easy to understand and maintain etc.

---

### Post by Wybiral on 2007-01-18
I support Mirrorball's approach... Working from up to down seems the most logical. Python is easy, but can tend to cradle you too much... C++ can often resemble python, but requires you to think more about type safety and handle data a little different. C is even closer to the machine and really makes you think about the structure of things.

And then assembly allows you to understand why your programs do the things they do, and gives you a more enlightened perception of how the processor interprets your programs. Assembly also teaches you how to make the most out of your programs and optimize for speed and size... Then you can start disassembling your C programs and gain a greater understanding of how the compiler works and use that knowledge to write more productive programs.

---

### Post by lnostdal on 2007-01-18
Stay away from C++; use C instead when needed (99% of the time you don't) and use a cleaner high-level language instead of C++ combined with clean C (which is not almost practically impossible to interface with from high-level languages). Do not listen to naive young people telling you C++ is the "ultimate ****" and the be all and end all of languages; it is not.

However C (and even some understanding of ASM) can be usefull to learn and understand; but if you need/want to have fun, focus on productivity and not poke with boring details for hours - stick with Python, Ruby, Java and Lisp.

In short; combine a clean strong low-level language with a clean strong high-level language and stay away from messy hybrids like C++. C is an example of a clean low-level language, while Python, Ruby and Lisp are examples of clean high-level languages.

My advice? Goolge for:

* htdp
* sicp
* "programming from the ground up"
* ..and "practical common lisp"

..all free. Or just stick with "programming from the ground up" and Python; there are probably many free and good programming books about Python also.

..my 2c..

---

### Post by Mirrorball on 2007-01-18
I disagree with you about C++. C++ is messy, but it's fast and  object-oriented. C isn't object-oriented, but it's fast and clean. Python isn't fast, but it's clean and object-oriented.

Besides, most good C programs compile as C++ programs. Everything you can do with C that you can do with C++ identically.

---

### Post by lnostdal on 2007-01-18
> **Mirrorball said:**
> C++ is messy, but it's fast and  object-oriented. C isn't object-oriented, but it's fast and clean. Python isn't fast, but it's clean and object-oriented.

Yup - and the majority of computation-time isn't spent taking high-level decisions; thus write tight inner loops in C (where the majority of computation-time is spent) and take high-level decisions (OOP etc...) in another language with way better support for this than both C and C++. This works great; just write everything in a clean high-level language first then pull out the small tight inner loop-parts at last (optimize last) then rewrite them in C -- if even needed.

You get everything:

* clean (what usually turns out to be the most important thing in most non-trivial cases in all phases)
* fast (which gets more important in the end-phase.. oh, as a bonus; with a clean design it turns out it is easier to optimize)
* ..and oop (and other cool high-level features)

---

### Post by Wybiral on 2007-01-18
The only complaint I have with C++ over C is how it compiles... Name mangling... I can look at an assembly dump of a C program and make perfect sense of it, but try looking at an assembly dump of a c++ compiled program... Yuck!

But, I don't have any problem with the language. It makes perfect sense to me and it gets the job done.

---

### Post by Mirrorball on 2007-01-18
> **lnostdal said:**
> Yup - and the majority of computation-time isn't spent taking high-level decisions; thus write tight inner loops in C (where the majority of computation-time is spent) and take high-level decisions (OOP etc...) in another language with way better support for this than both C and C++. This works great; just write everything in a clean high-level language first then pull out the small tight inner loop-parts at last (optimize last) then rewrite them in C -- if even needed.
I used to do this, but when you have to write too much C code, it's just easier to write it directly in C++.

---

### Post by Kingsley on 2007-01-18
I'm starting off with Java. Anybody know if it's easier than C or C++?

---

### Post by lnostdal on 2007-01-18
> **Kingsley said:**
> I'm starting off with Java. Anybody know if it's easier than C or C++?

Yes, it is -- go for it.

---

### Post by Wybiral on 2007-01-18
Personally I don't think Java is easier than plain C... C++ *maybe*

---

### Post by kinson on 2007-01-18
> **Kingsley said:**
> I'm starting off with Java. Anybody know if it's easier than C or C++?

I don't know about others, but I think its easier than C++. I kinda like Java :)

Cheers,
Kinson

---

### Post by pmasiar on 2007-01-18
I read somewhere (either Spolsky or Graham IIRC) about OOP, dynamic typing, dynamic memory management, and test driven/agile/XP approach. He claimed that OOP promise in increased productivity mostly failed - 95% of the increase is due by dynamic memory management + garbage collection, not OOP. 

For development to be agile, you need it test-driven, so refactoring is feasible. If you have that, you can rapidly assess design variants with fast prototyping language like Python, profile performance, and reimplent for speed in C, avoiding what he said "object-obsessed programming" :-) in Java.

So yes, Java is easier than C++ - because of GC.

---

### Post by hod139 on 2007-01-18
Hasn't this question been asked way too many times with the same end result? The original poster does not get the answer he or she was looking for, and the same group of regulars arguing about which language is best.

I'm going to stick with choosing the right language for the right job.  What task are you trying to solve?  Are you trying to write a simple GUI application, some numerical solver, micro controller, etc.  After answering that question then *maybe* you will get some agreement among the best language (I still doubt it though).  The fact that there are so many languages out there should tell you something.  Try to think of it this way, programming languages are to computer scientists what telescopes are to astronomers.  It is more important to learn the general concepts of programming, and then later apply these concepts to a specific language.

---

### Post by kinson on 2007-01-18
> **hod139 said:**
> What task are you trying to solve? 

I think he wanted a "good language to learn programming" or something like that. So I'm assuming a simple language for a beginner to learn that teaches them good practices... :D

I heard Python is good for beginning(I plan to try soon). If not, I'd recommend Java. (And the author has already tried both, so I'm redundant here :p )

btw, I do agree that every "what language to use" thread more or less ends up in debate of X language is better than Y language :p

---

### Post by hod139 on 2007-01-19
> **kinson said:**
> I think he wanted a "good language to learn programming" or something like that. So I'm assuming a simple language for a beginner to learn that teaches them good practices... :D
Good practices are never going to be taught by a language.  You (and not just you, but many others) have it backwards.  First comes the good practices, last the language. 

As for why it is important to identify the problem first before arguing about the language. What, if he or she wants to work with the new [iRobot Create?]("http://www.irobot.com/sp.cfm?pageid=292")  Then all this discussion about Java, C++ becomes mute since they only have a tiny microcontroller and you need a low level language.

How would you answer this (somewhat unrelated) question:  How good is your xxx algorithm?  Does it matter what language you used to answer this question?

---

### Post by kinson on 2007-01-19
> **hod139 said:**
> Good practices are never going to be taught by a language.  You (and not just you, but many others) have it backwards.  First comes the good practices, last the language. [quote]

I meant something like not VB6 :p You could pick up all sorts of bad habits.. :p If you know absolutely nothing about programming, then you'll need *somewhere to start. I don't think you can just teach practices(well, not much) without a language right? :-k 

[quote]
As for why it is important to identify the problem first before arguing about the language. What, if he or she wants to work with the new [iRobot Create?]("http://www.irobot.com/sp.cfm?pageid=292")  Then all this discussion about Java, C++ becomes mute since they only have a tiny microcontroller and you need a low level language.

How would you answer this (somewhat unrelated) question:  How good is your xxx algorithm?  Does it matter what language you used to answer this question?

I understand what you're getting at here. I agree :)

---

### Post by Wybiral on 2007-01-19
I think you learn "good habits" from multiple languages, otherwise you are usually just learning that language...

---

### Post by lnostdal on 2007-01-19
> **pmasiar said:**
> So yes, Java is easier than C++ - because of GC.

Yes, I agree -- OOP isn't the main problem (or solution or whatever). Before all this; memory and resource management is a way harder design problem to do properly without GC IMHO. 

I'm still running Ubuntu Dapper; almost all recent updates/fixes are patches for memory-problems (potential security risks etc.) in C/C++-software - most likely because of a lack of GC!

Guess where GC - like a lot of other cool ideas, come from btw.... :)
[http://en.wikipedia.org/wiki/Garbage_collection_%28computer_science%29](http://en.wikipedia.org/wiki/Garbage_collection_%28computer_science%29)

..note the part stating that GC can run faster than manual memory management in some cases -- and that some languages/implementations has support for both manual memory management and GC.

---

### Post by hod139 on 2007-01-19
> **Wybiral said:**
> I think you learn "good habits" from multiple languages, otherwise you are usually just learning that language...

How do multiple languages teach good habits?  Good habits for object oriented languages are usually bad habits in functional or imperative languages.  Think of it this way, if a child grows up in a bilingual house and hears and speaks both languages, how well do they know how to spell, or proper grammar?  These concepts cannot be learned from hearing or speaking the language. 

Programming languages are similar, they cannot "teach" anything.  They are the tool that the programmer with all his/her knowledge uses to make something.

[quote=kinson]
I don't think you can just teach practices(well, not much) without a language right?
[/quote]

There is some truth to that, but the language choice matters little (Some people will disagree and claim that certain languages make better teaching languages and others better industry).  For example Don Knuth invented his own language in his "The Art Of Computer Programming" series, which is considered by many to be the best series for computer scientists.  Arguable one of the best Algorithms book ([Intro to Algorithms]("http://www.amazon.com/exec/obidos/ASIN/0262032937/qid=997024331/sr=1-4/ref=sc_b_4/104-2626859-5069523") by CLRS) uses pseudo-code for implementing its algorithms.

---

### Post by rai4shu2 on 2007-01-19
If you can read a cookbook, you can program. Same basic principles. Preparation, procedure, what to expect if you screw up.

---

### Post by hod139 on 2007-01-19
> **rai4shu2 said:**
> If you can read a cookbook, you can program. Same basic principles. Preparation, procedure, what to expect if you screw up.
There are some problems with this thinking.  Programmers should be able to do more than just implement someone else's algorithm (recipe).  They should know how to write their own algorithms and how to analyze them.  A cookbook doesn't teach you how to make a new recipe or how good a recipe is.  That's why chefs go to school, to learn how to make their own recipes.  Similarly, that's why computer scientists go to school, to learn how to design good algorithms and how to analyze them.

---

### Post by rai4shu2 on 2007-01-19
Generally speaking, that is how you learn to design good algorithms. Not everyone is born with an innate understanding of data structures or mathematical models.

---

### Post by hod139 on 2007-01-19
> **rai4shu2 said:**
> Generally speaking, that is how you learn to design good algorithms. Not everyone is born with an innate understanding of data structures or mathematical models.
I disagree with your first sentence, but wholly agree with your second. Personally, I don't believe someone new to computer science with little to no understanding of data structures and mathematical modeling will magically learn these concepts from looking at what other people have done.  This is what school is for.  These concepts have to be learned in a formal systematic fashion.  In a computer science curriculum, algorithm design is not generally taught to first year CS students.  As you said, students have to learn data structures and mathematical analysis to build a foundation of knowledge before they start designing and analyzing algorithms.

---

### Post by bswilson on 2007-01-19
> **Tomosaur said:**
> I think you just answered your own question. Whichever you like best. Python may not prepare you very well for other languages though, it may be TOO easy and clean.

Is learning Python easier than plain 'ole UNIX shell scripting?  I have become somewhat proficient at writing shell scripts, sometimes using perl to do stuff...  Should I invest some time with Python?

---

### Post by Mirrorball on 2007-01-19
No, I don't think it's easier. But Python is a real programming language, you can do anything with it.

---

### Post by ghostdog74 on 2007-01-19
> **bswilson said:**
> Is learning Python easier than plain 'ole UNIX shell scripting?  I have become somewhat proficient at writing shell scripts, sometimes using perl to do stuff...  Should I invest some time with Python?

why don't you try it out and see for yourself? For me, I switched from shell/perl to Python and have been stuck with Python ever since. Imagine for example: 
```

print $^O 

```
shows you the OS platform in Perl. In Python, its more verbose
```

import sys
print sys.platform

```

but to me , its more readable. I don't want to look at my Perl script 1 year later to see $^O and wondering what is that without referring to a Perl reference book. Anyway, its just an example and also its purely my own preference and choice of language.  You have got to find your own resolve. :)

---

### Post by rai4shu2 on 2007-01-19
> **hod139 said:**
> This is what school is for.  These concepts have to be learned in a formal systematic fashion.  In a computer science curriculum, algorithm design is not generally taught to first year CS students.

Politics. :rolleyes:  Believe whatever you want. I'll follow what decades of scientific research has discovered.

---

### Post by hod139 on 2007-01-19
> **rai4shu2 said:**
> Politics. :rolleyes:  Believe whatever you want. I'll follow what decades of scientific research has discovered.
I would be interested in seeing some of this scientific research.  The only research into computer science education I know of is from the [ACM]("http://www.acm.org/education/curricula.html").

---

### Post by Wybiral on 2007-01-19
Multiple programming languages teach good habits because the cause you to solve problems differently in them... They force you to look at problems different.

---

### Post by hod139 on 2007-01-19
> **Wybiral said:**
> Multiple programming languages teach good habits because the cause you to solve problems differently in them... They force you to look at problems different.
I agree that they force you to look at problems differently, but how does that teach good habits?  I can solve the problem differently but poorly in every language that I try.  Languages can't teach anything, they are a tool.   These good habits can be learned, but any language will suffice.  Once learned, the good techniques can be carried into a variety of languages (after learning the specific syntax).

[What's with some of these super annoying Smilies available now?]

---

### Post by Wybiral on 2007-01-19
:guitar: :lolflag: ):P 

> [What's with some of these super annoying Smilies available now?]

I have no idea...

Anyway... Learning to solve problems differently is a good habit. Eventually you find the type of algorithms that work the best and the type of programming style that you feel the most comfortable with. You can't learn these things if you stick with the same language for too long, you will become spoiled and only think of things one way.

Seeing things from different perspectives IS a good habit in my opinion.

---

### Post by pmasiar on 2007-01-20
> **hod139 said:**
> I agree that they force you to look at problems differently, but how does that teach good habits?  I can solve the problem differently but poorly in every language that I try.  Languages can't teach anything, they are a tool.   These good habits can be learned, but any language will suffice.  Once learned, the good techniques can be carried into a variety of languages (after learning the specific syntax).


You are 50% right, but not 100%. I would argue that: 
1) some languages (Python) will guide you to create simpler, more readable programs, 
2) some languages' communities and cultures are very open to and leaning towards hackish solutions (perl, PHP), 
3) some are neutral, and with compliance to best practices,programs  can be very readable (C/Java), 
4) and some are so flexible and abstract that only the best gurus can create elegant solutions (Lisp, Forth), and rest of us just look in awe.

---

