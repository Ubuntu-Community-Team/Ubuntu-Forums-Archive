---
title: "Hidden gems: Advanced reading about language design and programming"
date: 2008-01-18
forum: Programming Talk
---

### Post by pmasiar on 2008-01-18
I'll like to start this thread to collect interesting articles any of us found. Idea is to get advanced topics, separate them from more beginners-related posts in stickies (and possibly make it sticky later). 

So it is aimed more towards people with experience   (although beginners are welcome). Poster could post summary, and I hope to avoid flamewars - if heated discussion is taking place, please start own thread :-)

Edit: yes, send me msg about better name for this feature, I'll ask admins to change it.

--------------------

Steve Yegge: [Code is the worst enemy](http://steve-yegge.blogspot.com/2007/12/codes-worst-enemy.html)

Steve thinks about 500KLOC codebase of game he maintains singlehandedly, and lessons he learned. Compares code to dirt, and refactoring to shuffling dirt around. Suggests that solution is not more design patterns or better IDE which manages more "dirt", but language allowing to "compress dirt" and work with higher abstractions on smaller codebase.

"[languages with] dynamic features make it more difficult for IDEs to work their static code-base-management magic. IDEs don't work as well with dynamic code features, so IDEs are responsible for encouraging the use of languages that require... IDEs. Ouch"

He still likes JVM, so his answer is Rhino - EcmaScript Edition 4.

---

### Post by Wybiral on 2008-01-18
> **pmasiar said:**
> ... Steve Yegge: [Code is the worst enemy](http://steve-yegge.blogspot.com/2007/12/codes-worst-enemy.html) ...

Good article!

---

### Post by Martin Witte on 2008-01-18
An interesting view on design patterns: [http://www.sdtimes.com/article/column-20080115-04.html](http://www.sdtimes.com/article/column-20080115-04.html)

---

### Post by RIchard James13 on 2008-01-18
Weblog/news site programming theory/computer science (very theoretical stuff)
[http://lambda-the-ultimate.org/]("http://lambda-the-ultimate.org/")

More concrete are many of the articles on the Dr Dobbs Journal Site
[http://www.ddj.com/]("http://www.ddj.com/")
Though you might have to do some digging to find what you want there.

For example go back in the archives to 2000 and you can find
"The Fastest Sorting Algorithm?"
> the algorithm presented in the paper "Sorting In Linear Time?" by A. Andersson, T. Hagerup, S. Nilsson, and R. Raman (Proceedings of the 27th Annual ACM Symposium on the Theory of Computing, 1995). It sorts n integers in time proportional to n log log n. In this article, I'll give you a complete description of this algorithm.
[http://www.ddj.com/architect/184404062]("http://www.ddj.com/architect/184404062")

> July 01, 2003
What's Holding Up the Roof?
[http://www.ddj.com/architect/184415002]("http://www.ddj.com/architect/184415002")

---

### Post by pmasiar on 2008-01-20
[size=+2]Difference between accidental and essential (inherent) complexity in programs[/size]

3 blog posts from same author.

[accidental](http://en.wikipedia.org/wiki/Accidental_complexity) complexity is not the same as [essential](http://en.wikipedia.org/wiki/Essential_complexity) (inherent) complexity in programs.  [Explanation, with relation complexity to abstraction](http://weblog.raganwald.com/2007/07/abbreviation-accidental-complexity-and.html) and how abstraction can add complexity.

[ Economizing can be penny-wise and pound foolish](http://weblog.raganwald.com/2006/12/economizing-can-be-penny-wise-and.html) - colorize different parts of code in red, yellow and green. Good frameworks puts yellow code into "infrastructure part" (which you, once debugged, do not touch) and out of our custom code.

We cannot remove essential complexity (only accidental one), but we can squeeze it out to framework, so our own code is green, and does not couple with yellow code.

"Programming languages teach you not to want what they cannot provide."&#8212;Paul Graham, author of concept of [blub](http://en.wikipedia.org/wiki/Blub) (the only hypothetical programming language with wikipedia entry AFAIK :-) )

Another example of accidental complexity is [golf about bug in code with 3 nested loops](http://weblog.raganwald.com/2007/12/golf-is-good-program-spoiled.html) and how language with more expressive power can avoid the bug completely.

"And the only way to break out of Blub is to cross-train, to really learn new languages. Otherwise, how will you know if your code could be shorter in a good way?"

"Shorter code is better if it expresses underlying relationships,...If it is shorter by  exploiting language tricks that do not reflect underlying relationships in your programs, that is bad"

---

### Post by melopsittacus on 2008-01-21
Stevey is right, large code can cause problems. I still cannot  see however how any programming language can decrease the size of the code significantly. The 50%-75% he mentions seems a little bit too much, but we are going to see if he succeeds. If he does, I am going to try out EcmaScript myself :) (By the way, JavaScript has been developed from Ecmascript, hasn't it?)

--

Anyway, here is another article that is funny, but might also teach something:

[http://www.freevbcode.com/ShowCode.Asp?ID=2547](http://www.freevbcode.com/ShowCode.Asp?ID=2547)

---

### Post by Wybiral on 2008-01-21
> **melopsittacus said:**
> Stevey is right, large code can cause problems. I still cannot  see however how any programming language can decrease the size of the code significantly. The 50%-75% he mentions seems a little bit too much,

From a language like Java to something like Ruby or Python... I would absolutely expect to see that kind of difference in the code size. Think about the shear difference in verbosity and the lack of type-restrictions. I'm not sure about ECMAScript though, it doesn't seem that much better off, but he's using a different ECMA standard than Javascript (which I don't know anything about), so maybe it's been improved since then.

---

### Post by aks44 on 2008-01-21
> **melopsittacus said:**
> Anyway, here is another article that is funny, but might also teach something:

[http://www.freevbcode.com/ShowCode.Asp?ID=2547](http://www.freevbcode.com/ShowCode.Asp?ID=2547)

:lolflag:
> Hungarian Notation is the tactical nuclear weapon of source code obfuscation techniques; use it! Due to the sheer volume of source code contaminated by this idiom nothing can kill a maintenance engineer faster than a well planned Hungarian Notation attack.


Reminds me of the [Uncle Screwpole series]("http://search.regdeveloper.co.uk/?author=Phil%20Rice")... :) (quite worth reading too)
This series is about the evil "uncle Screwpole" that gives advices to his nephew about how to screw his software projects. Contains several good project and team management advices, as long as you do the opposite of what is actually written. ;)

---

### Post by wolfbone on 2008-01-21
> **melopsittacus said:**
> Stevey is right, large code can cause problems. I still cannot  see however how any programming language can decrease the size of the code significantly. The 50%-75% he mentions seems a little bit too much

Roughly speaking, the more Lisp-like a language is, the more crap and repetition you can abstract away, the less buggy your programs are, the faster you can get things done, and the harder the problems you can tackle and solve. Paul Graham keeps going on about this in his essays, e.g. this one: 

[http://www.paulgraham.com/icad.html](http://www.paulgraham.com/icad.html)

Hardly anyone listens of course - and that's good for companies like ITA, but bad for FOSS Lisp.

---

### Post by uljanow on 2008-01-21
> **melopsittacus said:**
> Stevey is right, large code can cause problems. I still cannot  see however how any programming language can decrease the size of the code significantly. The 50%-75% he mentions seems a little bit too much, but we are going to see if he succeeds.

Reducing the complexity of software will lead to software that solves more complex problems (e.g. Assembler vs. OOP). There will always be software larger than one mind.

---

### Post by pmasiar on 2008-01-22
[size=+3]KISS principle and why "worse is better"[/size]

Another gem: [talk about KISS principle](http://adambosworth.net/2004/11/18/iscoc04-talk/) : why "perfect and rigid" systems decay and "flexible, simple, sloppy" survive. 
[found here](http://dotnetjunkies.com/WebLog/sriram/archive/2004/11/18/32707.aspx) (with additional comments)

If you want get full scoop what might happen to your project if you don't follow KISS, read about history of Xanadu ("perfect" predecessor of WWW): [The Curse of Xanadu](http://www.wired.com/wired/archive/3.06/xanadu_pr.html) - how Xanadu sucked dry couple of true believers. Spectacular failure, which took 20 years to happen.

**Edit:** 

[http://en.wikipedia.org/wiki/Worse_is_better](http://en.wikipedia.org/wiki/Worse_is_better) ("New Jersey approach") and [The Rise of "Worse is Better''](http://www.jwz.org/doc/worse-is-better.html) and [how it happened](http://dreamsongs.com/WorseIsBetter.html)
- Simplicity-the design must be simple, both in implementation and interface. It is more important for the implementation to be simple than the interface. Simplicity is the most important consideration in a design.

Author claims that "Worse is better" beats "MIT/Stanford approach" (do the right thing, however complicated it is).

---

### Post by pedro_orange on 2008-01-23
I wouldn't say this is entirely orientated around programming, but I have a book entitled "Best Software Writing I" Selected and introduced by Joel Spolsky- which is a collection of articles written by developers.

There is a few especially good articles in there including an interesting article on Python suggesting why white space should matter and how C++ sneakily became the defacto language at the expence of C, by supporting C! 

It seems these boards are full of python developers so I'll stick the link provided in the book for the python article (although I cannot check if it works since I'm at work)

Ken Arnold - Style is Substance: [http://www.artima.com/weblogs/viewpost.jsp?thread=74230](http://www.artima.com/weblogs/viewpost.jsp?thread=74230)

Enjoy

---

### Post by pmasiar on 2008-01-24
> Style is Substance

Good article. But you are mistaken, style is NOT a problem for Python (style is standardized, exactly like author proposed). Suggestion of the article is, all other languages should adopt single style, and author arguments why. From my experience in Python, it makes perfect sense to me.

**Edit**
I added "worse is better" to #11, post about KISS.

---

### Post by pmasiar on 2008-01-25
[size=+3]Programming style and thinking style[/size]

[5 thinking styles](http://www.manageability.org/blog/archive/20030430%23thinking_styles_and_software_engineering/view) and how [different languages express different thinking styles](http://www.manageability.org/blog/archive/20030502%23the_perfect_thinking_style_for/view). 

- different styles of thinking apply to different kinds of problems. 
- dynamically typed languages and [prototypes are like Tracer Bullets](http://www.artima.com/intv/tracer.html): If you got a moving target you use tracer bullets

Check also [Good enough software](http://www.artima.com/intv/goodenough.html) - debunking the myth we can write ug-free software. Space shuttle code was cost $1K per line to develop! Another discussion with author of "Pragmatic Programmer:  From Journeyman to Master"
- "Heisenberg effect : The act of introducing the system changes how the users work."

Myers-Briggs test shows also surprising differences - especially when you compare what is "obvious" for two different groups. I recommend everyone to know your type and know consequences for your communication style.

---

### Post by pmasiar on 2008-01-27
[size=+3]Design patterns, syntax sugar, and language development[/size]
Interesting article by Mark Dominus [Design patterns of 1972 ](http://blog.plover.com/2006/09/11/)

Mark muses about design patterns. He shows how in C you can informally implement "object-oriented class" with public/private members and inheritance, and how the same thing is implemented in C++ directly in syntax, so it is invisible.

Another example of "pattern" is subroutine, as it was invented in Assembly in 1957. I remember BALR 14 was just this, and always was curious how it fits. Now I know. :-)

> 
many patterns aren't really addressing recurring design problems in object-oriented programs; they are actually addressing deficiencies in object-oriented programming languages, and that in better languages, these problems simply don't come up, or are solved so trivially and so easily that the solution doesn't require a "pattern". In assembly language, "subroutine call" may be a pattern; in C, the solution is to write result = function(args...), which is too simple to qualify as a pattern.
...
The stance of the "Design Patterns" movement seems to be that it is somehow inevitable that programmers will need to implement Visitors, Abstract Factories, Decorators, and Façades. But these are no more inevitable than the need to implement Subroutine Calls or Object-Oriented Classes in the source language. These patterns should be seen as defects or missing features in Java and C++. [b]The best response to identification of these patterns is to ask what defects in those languages cause the patterns to be necessary, and how the languages might provide better support for solving these kinds of problems. 

... Instead of seeing the use of design patterns as valuable in itself, it should be widely recognized that each design pattern is an expression of the failure of the source language.[/b] 

If the Design Patterns movement had been popular in the 1980's, we wouldn't even have C++ or Java; we would still be implementing Object-Oriented Classes in C with structs,


So ie. Iterator pattern from Java is just list comprehension in more dynamic language like Python, no need for a pattern, like you don't need pattern for subroutine call.

Found via [Fifty Years of Software Development](http://www.codinghorror.com/blog/archives/000686.html) (with nice poster of history of language development and influences). Article notices: 
> Redwine and Riddle reviewed a number of software technologies to see how they develop and propagate. They found that it typically takes 15-20 years for a technology to evolve from concept formulation to the point where it's ready for popularization. 
So design patterns are on the edge of becoming mainstream. Time to get learning new languages, which implement those patterns in syntax :-)

---

### Post by pmasiar on 2008-01-31
[The code monkey's guide to cryptographic hashes](http://www.linuxworld.com/cgi-bin/mailto/x_linux.cgi?pagetosend=/export/home/httpd/linuxworld/news/2007/111207-hash.html) - in language that any programmer (and even some managers) can understand. By kernel hacker and LinuxChix founder Valerie Henson.

"Used properly, content-based addressing dramatically reduces bandwidth use, simplifies code, and improves security. But used when it doesn't make sense, it can reduce performance, increase bandwidth usage, and create new security risks."

With interesting graphs about life stages of cryptographic functions, timeline for common functions, and speed comparison.

Edit: [+ some scientific disagreement](http://www.cs.colorado.edu/~jrblack/papers/cbh.html) with different article by Val, explaining why this one is true. :-)

---

### Post by pmasiar on 2008-04-30
Perfect storm: many changes are coming, simultaneously: [Inflection points](http://blog.isotoma.com/2008/04/inflection_points_1.html). Hold your hats!

---

### Post by pmasiar on 2008-10-15
[Static Typing, Dynamic Language Performance, V8 and Tracing JITs](http://www.voidspace.org.uk/python/weblog/arch_d7_2008_09_06.shtml#e1010)

Interesting read about execution speed in dynamically typed languages. Quotes:

"Only a subset of all possible programs can be written with statically typed languages. For some people that is enough."

"For optimisation, more is known about a program written in a dynamically typed language at runtime than is known about programs in statically typed languages at compile time"

With links to articles about how V8 (new Javascript engine by Google) is so much faster, and how tracing JIT compiler (like PyPy) can make dynamic language **faster** than traditional statically compiled code (and why PyPy is not written in C). Cool stuff.

---

### Post by cmay on 2008-10-15
thanks.

---

