---
title: "Math, Math Math"
date: 2009-03-04
forum: Programming Talk
---

### Post by Xoanan on 2009-03-04
Hi All

I am new to programming world, so I did some lurking around here and searching and I have read various posts from several people here. A lot of them stress Math. 

I discovered after delving into Python why this is necessary.  I vaguely remember working with complex numbers and imaginary numbers back in my college days, but I never used them again. 

At this point, I am going to have a friend pop over and help me with it(as she is working on that class now).  I have also gone to some websites for further assistance

Here's one
[http://www.purplemath.com/modules/]("http://www.purplemath.com/modules/")

I know there are more.  

My friend got a copy of _Idiot's Guide to Algebra_ from the library for help.  

If you have any other suggestions for resources, please feel free to post here. 

Thanx

Xoanan

---

### Post by Tony Flury on 2009-03-04
To be honest - it depends what you need/want to program. I have just finished writing a Graphical front end in Python for flickr - so i can upload pictures from my PC to flickr. The most complicated maths in that application was an increment (adding 1 to a value).

I have been in the s/w industry for 20 years (writing significant code for significant industrial strength applications), and i have never needed things like matrices, complex numbers etc.

Many applications will not require any complicated maths at all, and some will require a lot (3d modelling, games for example).

If you are not confident about complex maths etc, then don't worry - learn what you need when you know you actually need it.

---

### Post by nateperson on 2009-03-04
I can't speak from experience, but as I work on a second B.S. in Computer Science, they are requiring me to take Discrete Math and Linear Algebra.  They don't care much one way or the other about how I've already done higher maths, just those as those course seem geared towards the Comp Sci field.

Nate

---

### Post by sujoy on 2009-03-04
other than simple arithmetic, you can really take on the mathematical side as and when you encounter any problem with it.

having said that, if you are willing to spend time learning it anyways, go through discrete maths, set theory, and graph theory. these will help you understand many algorithms better :)

---

### Post by cmat on 2009-03-04
If you think about it a program is a giant collection of math equations/functions that do stuff when certain conditions are met. I find myself deriving formulae for certain applications. You won't need anything more than algebra in most cases. Since you have iters and loops calculus isn't needed. 

Taking calculus just makes you better at problem solving, really not much use when you are making database clients and stuff.

---

### Post by simeon87 on 2009-03-04
It's probably better to learn the maths when you discover that you need it. Of course, you'll need some basic maths, like algebra, but for average desktop applications, the needed math won't be that complicated. Only if you intend to write (or asked to write) an application that will require certain mathematical techniques, it's good to study them beforehand but for the rest, you'll discover what you need while developing.

---

### Post by konqueror7 on 2009-03-04
just a good foundation in algebra is good enough, in regards to other maths, you will only need it on specific situation as mentioned above. and above all, math only wants to make you a problem solver, in which case, what developers do...

---

### Post by CptPicard on 2009-03-04
Well, all the important stuff is said here already, but I would like to specifically stress the point that getting comfortable with reading basic mathematical "formalism" -- logic and set theory -- helps a lot with reading algorithm descriptions from texts. Imperative-style pseudocode requires a lot more "parsing and mental execution" in order for you to actually figure out what the core idea of the algorithm is. It's no surprise undergrad textbooks rely more on "real programming language" style pseudocode descriptions (which is *work* to read) while the more advanced books don't.

This is, by the way, one of the reasons why I really like the way you do stuff in functional programming, too. It just makes things very clear, although it may not seem like it to the uninitiated.

---

### Post by Crimsonblah on 2009-03-04
I agree with konqueror regarding the fact that most math you need to learn is specific. If you're ever dealing with vision applications, understanding linear algebra and matrix multiplication are very important.

Check out OpenCV if you're interested in real time computer vision applications - [http://opencv.willowgarage.com/wiki/](http://opencv.willowgarage.com/wiki/) or just google OpenCV.

---

### Post by Reiger on 2009-03-04
> **CptPicard said:**
> This is, by the way, one of the reasons why I really like the way you do stuff in functional programming, too. It just makes things very clear, although it may not seem like it to the uninitiated.

Yeah, functional languages really have that certain something where you find yourself staring in amazement at how simple a solution to your first-time encounter of a problem turned out to be after battering your mind against it for god-knows-how-long. Plus: the performance of a solution can be easily gauged from its structure.

---

### Post by nvteighen on 2009-03-04
> **CptPicard said:**
> 
This is, by the way, one of the reasons why I really like the way you do stuff in functional programming, too. It just makes things very clear, although it may not seem like it to the uninitiated.

That's because you eliminate the state variable. It's obvious: you don't need to take account on what the values are in which moment, but just how the relation is constructed.

It's fantastic, of course. :D

---

### Post by kjohansen on 2009-03-04
I think you need to make a distinction between computer science and software development.  If your goal is software development the math isnt useful.  But if you are in a pure computer science field you will need the math.  Personally I do machine learning, and I do more math than programming.

---

### Post by PythonPower on 2009-03-04
[ Curry-Howard correspondence]("http://en.wikipedia.org/wiki/Curry-Howard_correspondence") has some relevance to this thread. Programming and maths overlap so much I cannot decide which I prefer - especially when I almost always do both together...

If you need somewhere to practise mathsy programming, see this link:

[http://projecteuler.net/](http://projecteuler.net/)

---

### Post by CptPicard on 2009-03-04
> **PythonPower said:**
> [ Curry-Howard correspondence]("http://en.wikipedia.org/wiki/Curry-Howard_correspondence") has some relevance to this thread.

Glad you're seeing the point. ;) (I need to remember that link, thanks) -- the links between provability and computability are interesting. They actually go all the way to the strong vs weak AI stuff, cognitive science... *and* through that to the symbolic-manipulation-systems and linguistics side of things (Chomsky is a linguist after all).

The software engineering vs. CS difference is certainly valid in a lot of ways. I programmed very little as a student, and most of the algorithms stuff worked on the level of "you're expected to be able to program this if need be, but it's the idea and math behind it that is interesting". However, even in CS one should get proficient at implementation.

Between the math-theory and the software engineering side of things ("mapping mind to computational solution") is the aforementioned language aspect of programming that is often ignored by a lot of people for various reasons (math geeks don't consider it important because of Turing-completeness, software development guys are just passionate about language X because it's "pragmatic" or "popular" or whatever) but is just getting clearer and clearer to me the more I actually program after leaving the ivory towers of academics.

Programs actually *say* something about some computational thing using *symbols*, and that is at the core of the philosophical questions and theoretical limitations of computation. Like incompleteness -- somehow, there seems to be external semantics to manually computable symbolic systems that renders them incapable of proving everything within the system, but yet, the mind sees this.

So of course I like having my symbolic system to at least be optimal in the sense of it serving my mind well, if I can't make the symbolic system itself become computationally stronger by switching symbols... the upside is that from the machine perspective, they're all just as valid, so I can pick and choose at will.

---

### Post by Xoanan on 2009-03-04
Thanx for all the info and links, gang!

Wow! Quite an interesting discussion!:popcorn:

---

### Post by Tomosaur on 2009-03-04
In my experience, you generally don't 'need' complex mathematics all that much, but it can be incredibly useful and save you so much time if you think about problems mathematically.

So long as you can identify patterns and rules mathematically, you should be able to save yourself time and effort when others would end up writing reams of code :P

---

### Post by s.fox on 2009-03-04
Pure maths is the way to go, followed by algebra.

---

### Post by jackmcslay on 2009-03-04
the only commonly-made type of software that may require complex math I can think of is games. If you're not doing these nor anything else that plays with heavy calculations (like, statistic calculations), there's little need to study a lot of math

---

### Post by monkeyking on 2009-03-04
It depends on so much.
If you just want to do php webpaging.
Then you will be happy with just knowing boolean logic.

If you like math,
then probly want a job where you will be programming more mathoriented stuff.

You should learn it because you think its funny or interesting.
Not because "its very important"

---

### Post by aszxcv on 2009-03-04
[http://steve-yegge.blogspot.com/2006/03/math-for-programmers.html](http://steve-yegge.blogspot.com/2006/03/math-for-programmers.html)

a good read he breaks down this topic

---

### Post by monkeyking on 2009-03-05
> **aszxcv said:**
> [http://steve-yegge.blogspot.com/2006/03/math-for-programmers.html](http://steve-yegge.blogspot.com/2006/03/math-for-programmers.html)

a good read he breaks down this topic
I absolutely dont agree with this guy.

```

They teach math all wrong in school.
Way, WAY wrong. If you teach yourself math the right way,
you'll learn faster, remember it longer,
and it'll be much more valuable to you as a programmer.

...
The right way to learn math is breadth-first, not depth-first. 
...

I went back and looked at the long-division algorithm
 they teach in grade school, and damn if it isn't
 annoyingly complicated. It's deterministic, sure, but you never have to do it by hand

```
Math for the sake of math,
is only about defintions, theorems and proofs.
this is the approach you will learn in school.
If you are not into the abstract deduction,
then you wan't applied mathmatics.

Someone likes depthfirst others breadthfirst.

I don't know anyone who don't know how to do a long div.

---

### Post by nvteighen on 2009-03-05
> **CptPicard said:**
> 
Between the math-theory and the software engineering side of things ("mapping mind to computational solution") is the aforementioned language aspect of programming that is often ignored by a lot of people for various reasons (math geeks don't consider it important because of Turing-completeness, software development guys are just passionate about language X because it's "pragmatic" or "popular" or whatever) but is just getting clearer and clearer to me the more I actually program after leaving the ivory towers of academics.

Programs actually *say* something about some computational thing using *symbols*, and that is at the core of the philosophical questions and theoretical limitations of computation. Like incompleteness -- somehow, there seems to be external semantics to manually computable symbolic systems that renders them incapable of proving everything within the system, but yet, the mind sees this.

So of course I like having my symbolic system to at least be optimal in the sense of it serving my mind well, if I can't make the symbolic system itself become computationally stronger by switching symbols... the upside is that from the machine perspective, they're all just as valid, so I can pick and choose at will.

From the Linguistics side, which is from where I can give a little account of, the panorama is also that worse. For some reason, Computational Linguistics and generally anything related to artificial languages is dismissed as a non-serious topic that's sometimes studied to prove points about natural languages.

Curiously, the only place where artificial languages make sense is computing. Think about it: there are several artificial languages being succesfully used by people not only to program stuff but also to show ideas (e.g. textbooks where an algorithm is written in some real programming language). On the other hand, languages like Esperanto, Interlingua, Klingon, etc. may be interesting but they can't claim the success programming languages have regarding adoption.

CptPicard's point is crucial, IMO: The machine doesn't care about what language you're using. At the end, it all gets down to binary... But the human does care about the language choice: You have a project and you may think "Do I use Python, C or Perl for this?"; and you choose trying to get the optimal symbolic system.

But we must be aware that programming languages are very open semantical systems where the most important features are those that are able to generate new meanings, not actually the base meanings the language includes. A program consists in using the word-formation processes the language gives you to create your own semantical system that maps to a certain reality the way you need.

---

### Post by kjohansen on 2009-03-05
[http://steve-yegge.blogspot.com/2006...ogrammers.html](http://steve-yegge.blogspot.com/2006...ogrammers.html)

His views sound somewhat similar to the basis of the "New Math" in the sixties.  Why would you ever want to teach a third grader axiomatic set theory???

---

