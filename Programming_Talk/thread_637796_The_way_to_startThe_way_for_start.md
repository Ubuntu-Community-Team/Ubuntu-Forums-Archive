---
title: "The way to start
The way for start"
date: 2007-12-11
forum: Programming Talk
---

### Post by Nin.Hernan on 2007-12-11
Hey, a few days ago I am interested in learning to program.
I am lost, people tell me a different way to start for example:

Start with:

Programming Paradigm.
Algorithms.
Data Structures

Some have told me that start with a programming language and then see algorithms but others say that the algorithms are important.
I started searching Python books, but according to those who saw not teach such important concepts (programming paradigms, which the machine understands 1 and 0, high-level languages, compiled, interpreted, etc.).

What do you think?.

Thanks

[RIGHT]Nin.Hernan[/RIGHT]

---

### Post by pmasiar on 2007-12-11
Start with a Python book for beginners. Later you can learn algorithms and data structures (and even different paradigms), but until you can code at least a little, it will not make any sense to you.

Wiki in my sig has links to books and training tasks.

---

### Post by Wybiral on 2007-12-11
This is a debatable question and is the cause of many flamewars around here :)

IMO, Python is a great starting point. If you find later that you need to understand the machine even more, then you can move from Python to C (at that point, you can write modules for your Python programs in C and take advantage of both languages).

It really depends what you want to do. If you want to write device drivers or do any kernel development, you probably will want to dive into C and Assembly.

If you want to start writing applications and get a feel for program design patterns and what programming is like, then something like Python is great. IMO it's a nice starting point because you can learn the higher level concepts right away, then you can learn various paradigms since it supports OOP, procedural, and functional. Then when you need to expand your knowledge to bits and bytes, you can use what you learned in Python to explore C (and use what you learn in C to expand your Python programs).

---

### Post by tyoc on 2007-12-11
> 
 Programming Paradigm.
 Algorithms.
 Data Structures

if you really gona start, I would suguest that you go for algorithms, but in the point of view of pseudocode and flow diagramas (try to give steps to how you will change the tyre of a car, do eggs, see that some of those things have repetitive things, but you dont write them 1 time after the other, you say some like "do this action until you cant doit, or more than 10 times"), know how to solve problems  (yes, all know how to solve something, but the point of write it, is that you can write a long description [how to do each step carefully at nauseum] or how to express it in ashort way) and what an algorithms is, then you can go to program (write actual solutions).

Paradigms are only models for model you write the actual solutions, but you would still be able to imagine a solution without a specific model in mind, or what, when you have a daily problem you say "o let me think it in OO, or procedural or functional or any other not so know paradigm" ;), no, you can solve the problem without think in those models.

Still models are important, because they mean some extra organization, like when you do poetry, you can write "prosa" but you can take some guides and write a sonet, or any other well know poetry "paradigm" ;).

---

### Post by Nin.Hernan on 2007-12-11
I am looking at the wiki and I met:

Byte of Python.
Python Tutorial at wikibooks.
Alan Gauld's book.
Hands-On Python A Tutorial Introduction for Beginners, by Andrew N. Harrington.

Which is the best?

Thanks.

[RIGHT]Nin.Hernan[/RIGHT]

---

### Post by pmasiar on 2007-12-11
They all are free online books (I seen gauld's book in BN tho) so you can try which style is best match for you. 

I am not beginner - you are, so I can only guess :-) Try them all: explaining the same thing in different ways might give you more insight, then tell us which one you liked most.

---

### Post by CptPicard on 2007-12-11
Guys, pmasiar is so right :) The OP is a total noob and those concepts he's mentioning in the post are something nobody can seriously suggest someone learn who doesn't know *anything* about programming.

Well ok, perhaps there is such a creature as a pure pencil and paper programmer who plays around with algorithms in his mind (I actually prefer that) but the OP needs to learn a programming language first. Any one of them, but probably Python.

---

### Post by tyoc on 2007-12-11
I not think is necessary to learn a programming language, after all programming is  not only about language (a great part is "dominated" by the choice), but I have seen people with great experience in sintaxis and things related to a language without the "imagination" for solve certain problems, thus that is why I would suguest first take a course where there is solution to problems, more in the context of own way of think instead of take any high, low, or quasi natural progrmming lang.

---

### Post by Wybiral on 2007-12-11
**CptPicard:**
It sounds like you've seen the light! :)

**tyoc:**
I do know what you're saying. But also consider that it's easier to test algorithms and program flow when you can actually run the program. Sure, you can write it all out and do it in your head, but to me it just makes more sense to be able to jump right in and see the consequences. Another large part of programming is being able to debug and understand the error messages the language spits at you when you mess up, you can't learn that without diving in.

---

### Post by CptPicard on 2007-12-11
> **Wybiral said:**
> **CptPicard:**
It sounds like you've seen the light! :)


No, I'm not a sworn-in member of the Python Cult yet... but I am not rabidly against the language either :) and as a beginner language it *is* good because of the straightforwardness. Which is good for non-beginners too.

> **tyoc said:**
> I not think is necessary to learn a programming language, after all programming is  not only about language

Being somewhat of a CS purist myself and a very lazy programmer (it tires my fingers or something) I would be the last one to suggest that it's "only" about the language --- actually you would be hard pressed to find anyone worthwhile claiming something like that. On a high, abstract level, I personally feel that indeed, the language is somewhat irrelevant as long as it practically fits the problem you're solving.

> but I have seen people with great experience in sintaxis and things related to a language without the "imagination" for solve certain problems

Those people are just simply incompetent then. Syntax is the easy part, but just because it is, it doesn't mean you can completely do away with it.

> thus that is why I would suguest first take a course where there is solution to problems, more in the context of own way of think instead of take any high, low, or quasi natural progrmming lang.

If you're not able to learn something as simple as Python's syntax, then you won't be able to pass that class either, and once you've got Python, you've got a tool to actually solve those problems for real.

---

### Post by pmasiar on 2007-12-11
Formal (programming) language is first a tool to formalize **your own** thinking and express it in a strong semantics, not in a wishy-washy form of colloquial language.

Of course it is enlightening experience to learn formal grammars, but trust me, things you can formally describe and parse (as formal grammar) in your head or with pen and paper during first semester are so boring you would cry.

Programming with real language is so much more fun - because you don't have to execute the steps in your head, computer does it for you.

If someone knows the syntax but cannot solve problems - he is a fraud (or theoretical computer scientist - no difference :-) ), not a programmer.

**In theory, there is no difference between theory and practice. In practice, there is.** :-)

---

### Post by tyoc on 2007-12-11
> But also consider that it's easier to test algorithms and program flow when you can actually run the program.+1, yea, but what happen when you don't have the idea of how to do a program? for example people come and say some like "is this problem [description here] good for start programming?" and normally people will see that is hard for a first try program for a beginner. They don't have enough experience for even choose the problems that they can handle now or tomorrow.

> but to me it just makes more sense to be able to jump right in and see the consequences> Another large part of programming is being able to debug and understand the error messages the language spits at you when you mess up, you can't learn that without diving in.later
> because you don't have to execute the steps in your head, computer does it for you.thought it is good to see the real consequences of your code, from my POV is best to design first, or at less stop to think something before you actually code, I mean, Im sure there is no programmer in the world that can sit and start writing code about a problem that hasn't took at less 1 second to think, but with beginer programmer I guess is what they try (sorry, I haven't started first coding directly to a lang for computer, thus I can't know) because they not only need to know the lang of choice, but also they need to learn how to organize a problem in functions, state transitions/variables, and other things related to a specific lang and also they need to manage to map the way that they "solve" the problem in the head with the lang in question and finally to the consequences.

Also I consider that the source of all errors is the source  code I not mean only sintaxis, free or not free resources, exceptions, but also the design and all that you can blame a program of. And that code come from the mind/person, thus I consider that not "executing" them in your head, you are loosing a great CPU processor to pass your program from.





> ... On a high, abstract level, I personally feel that indeed, the language is somewhat irrelevant as long as it practically fits the problem you're solving.
Yes, still you need to map your solution to the lang, and that mapping normally introduce errors apart of the errors  that you can have in the design, also it introduce some constraints it introduce "some say to say" things.

Have pass long time I don't use my "list" of what things I think people need to solve a problem, but IIRC they where: the problem, knowledge of the problem to solve subject/area, and understanding/thinking/separation of the problem, knowledge of the lang and paradigm and the constraints of the lang like and mapping of your way of think "ey I have in mind some like a = b+c+2, but Im using C and b is a list of x and is a structure that behaves like T why I can't do that?", your POV or perspective for solve it, the things at hand and knowledge/adaptability to them, mmm has pass to much time that I feel the list is uncomplete, but I will add the right questions for the problem (you know, the right questions guide you to the right answers).

> Those people are just simply incompetent then. Syntax is the easy part, but just because it is, it doesn't mean you can completely do away with it.perhaps I was ars when I say know the "sintaxis", but you get the idea, I know that for some people things are easier than for others, still think that they can be best if they first take a course like that.

> Formal (programming) language is first a tool to formalize **your own** thinking and express it in a strong semantics, not in a wishy-washy form of colloquial language.Still I return to what happen when you really don't know how to solve the problem, for instance how people will be able to make a simulation of a reactor for some "specific atoms", or an AI program that is able to learn what you taught to it and then the program teach it to other people, if you don't know the basic subjects, hardly if not "impossible" way that you can "visualize"/"adivine" all the things that are already there for you to learn and then to extend.

> Of course it is enlightening experience to learn formal grammars, but trust me, things you can formally describe and parse (as formal grammar) in your head or with pen and paper during first semester are so boring you would cry.Though I think we are talking about different things, I think that the following


> Of course it is enlightening experience to learn ... things you can... describe ... in your head or with pen and paperI give taht a +Infinite*Infinite :P.

---

### Post by CptPicard on 2007-12-11
Yet, there still is absolutely no reason to actively *keep* a complete noob from starting to learn basic programming because he is not yet "ready" to write perfectly designed reactor simulations or AI programs.

Programming is not rocket  science... application domains are. You're worrying about those prematurely if someone just wants to get started with coding. Stuff like proper arrangement of your code come with time, but you can't learn those without having some idea of the programming language you're actually using.

---

### Post by tyoc on 2007-12-11
> not yet "ready" to write perfectly designed reactor simulations or AI programs.mm, I think I was referring to some of you people that already know how to program for that case of reactors and AI that can learn and then teach to other persons, but I guess I not make it direct enough. And I was referring to that in the context of "the necessary to solve a problem" in a "list" of what I think is important my POV, and I think it apply from the most simple to the more complex.

Still it apply that what you call domain specific to a new person, because all this way to write something that has meaning to a computer is to new for them, all this new concepts look to specific.

>  Programming is not rocket  science... application domains are.Agree, but have seen lot of people and lot of question that make it look like that.

My point for make it clear, is that you need more things that a lang for solve a problem, and thought it is good to "formalize"  it (or let the thing execute it) writing down the code, also is good to use the brain for "compile" it before the fact, because you need to know the subject or merge/dive in to the problem (with the other points) for been at less able to start grasping the new thing, even that it is not as specific as simulations or AI.



Also Im not stoping it, you see my hand there?, it is only a POV.

---

### Post by pmasiar on 2007-12-12
> **tyoc said:**
>  but what happen when you don't have the idea of how to do a program?...(big snip) 

So many  words, so little sense.

Thats why we have books for beginners, which introduce programming by solving simple problems, no?

---

### Post by Wybiral on 2007-12-12
If you want to write pseudo-code, what better than python :)
You don't have to execute it if you don't want to, but python does make good pseudo-code.

---

### Post by slavik on 2007-12-12
OP, the first thing you should learn is what those words are that you mentioned. :)

Programming Paradigm = do you think in terms of things interacting with each other? or in terms of serial steps (one after the other)? or in terms of mathematical functions?

Algorithm = a way to do something (write down on a piece of paper what you do to get ready for school/work), there you got an algorithm of how to get ready for school/work. :)

Data Structures = ways to structure data (self explanatory IMO). Think about when you write an address on an envelope or the business letter layout and such.

As for the first language ... everyone knows what I will say so I will save everyone the "duh! he always says that!" moment (learn Perl :))

---

### Post by pmasiar on 2007-12-12
[http://en.wikipedia.org/wiki/Programming_paradigm](http://en.wikipedia.org/wiki/Programming_paradigm)
[http://en.wikipedia.org/wiki/Algorithm](http://en.wikipedia.org/wiki/Algorithm)
[http://en.wikipedia.org/wiki/Data_Structure](http://en.wikipedia.org/wiki/Data_Structure)

None of the above is relevant - for first month of learning Python, any tutorial has enough relevant info.

---

