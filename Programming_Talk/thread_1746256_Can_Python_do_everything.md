---
title: "Can Python do everything ?"
date: 2011-05-01
forum: Programming Talk
---

### Post by kevin11951 on 2011-05-01
I have been messing around with Python for the last month or so, and I am wondering: Can Python do everything?  For example, could I take a left eye image and a right eye image and convert them to a 3D (red-blue) image using strictly Python?

edit:  I am not looking for a way to actually complete the above problem, it's just an example...

---

### Post by nmaster on 2011-05-01
i'm not sure if openCV can do what you're looking for, but take a look:
 [http://opencv.willowgarage.com/documentation/python/index.html](http://opencv.willowgarage.com/documentation/python/index.html)

---

### Post by cgroza on 2011-05-01
Python is not that good with image processing because it is a thing where speed matters. Languages like C++ and Java are more useful there.

---

### Post by kevin11951 on 2011-05-01
> **nmaster said:**
> i'm not sure if openCV can do what you're looking for, but take a look:
 [http://opencv.willowgarage.com/documentation/python/index.html](http://opencv.willowgarage.com/documentation/python/index.html)

Aside from the edit, that really is interesting, and I will start messing with that soon...

---

### Post by Tahakki on 2011-05-01
You can find a module or library to do pretty much everything you can with another language - unless it's something like developing for another platform, Android for example. Python is also much slower than other languages. For things like your average program, though, it's perfect.

---

### Post by NovaAesa on 2011-05-01
Python CANNOT do anything. Try writing a Python program that takes as input another python program and returns true if that program halts and false if it doesn't halt. If you can successfully write such a program, I will purchase the program and rights to the associated algorithm off you for $10,000.

---

### Post by kevin11951 on 2011-05-01
> **NovaAesa said:**
> Python CANNOT do anything. Try writing a Python program that takes as input another python program and returns true if that program halts and false if it doesn't halt. If you can successfully write such a program, I will purchase the program and rights to the associated algorithm off you for $10,000.

How long is the wait time to see if it doesn't halt?

---

### Post by slavik on 2011-05-01
> **NovaAesa said:**
> Python CANNOT do anything. Try writing a Python program that takes as input another python program and returns true if that program halts and false if it doesn't halt. If you can successfully write such a program, I will purchase the program and rights to the associated algorithm off you for $10,000.
lowball much? ;)

---

### Post by juancarlospaco on 2011-05-01
yes, it can.

---

### Post by NovaAesa on 2011-05-02
> **slavik said:**
> lowball much? ;)

That's my entire life savings (I'm only 21), although I guess I could get a loan and offer $1,000,000 :P

---

### Post by nvteighen on 2011-05-02
> **NovaAesa said:**
> Python CANNOT do anything. Try writing a Python program that takes as input another python program and returns true if that program halts and false if it doesn't halt. If you can successfully write such a program, I will purchase the program and rights to the associated algorithm off you for $10,000.

Being a total ignorant in theoretical CompSci, I guess this has something to do with computability... But isn't this impossible in all programming languages?

---

### Post by Tony Flury on 2011-05-02
It is the Halting problem - which no-one has solved - nothing to do with programming languages - it is a fundamental problem in computer science.

given an arbitrary complex program and arbitrary inputs can you by inspection prove that the program will halt.

[http://en.wikipedia.org/wiki/Halting_problem](http://en.wikipedia.org/wiki/Halting_problem)

If you read the second paragraph - you will see that a generic algorithm has been proven to be not possible

> 
Alan Turing proved in 1936 that a general algorithm to solve the halting problem for all possible program-input pairs cannot exist. A key part of the proof was a mathematical definition of a computer and program, what became known as a Turing machine. We say that the halting problem is undecidable over Turing machines. It is one of the first examples of a decision problem.


---

### Post by NovaAesa on 2011-05-02
> **nvteighen said:**
> But isn't this impossible in all programming languages?
Correct, and in particular it's impossible in Python.

Python is capable of computing any computable function though (given sufficient memory and time), including the OP's anaglyph program.

---

### Post by ngrieb on 2011-05-02
Python is pretty nifty, but as mentioned above it is fairly slow at data processing. If you need speed use F90 or C. Large arrays and matrix problems are to say the least difficult to work with in python.

On a side note:
If anyone has any dev experience and knows anything about python GUI's I've been trying to get 2 pygtk applets to work for about half a year...and no one has helped me. I am also working on some plugins for GIMP (a true Multiresolution Transform plugin) and Blender (a simple shell routine for intersecting faces) using python, and might be in need of some assistance.

---

### Post by Tahakki on 2011-05-02
@ngrieb PM me with your PyGTK issues if you like.

---

### Post by slavik on 2011-05-02
Python can do everything. Same can be said for brainfuck.

---

### Post by ngrieb on 2011-05-02
@Tahakki,
Thanks, I really really appreciate it. I have been working on trying to update the GUI to one of them lately, but I think I have an older version tar balled up somewhere.

---

### Post by unknownPoster on 2011-05-02
> **nvteighen said:**
> Being a total ignorant in theoretical CompSci, I guess this has something to do with computability... But isn't this impossible in all programming languages?

Pretty sure it's one of the millennium problems too.

---

### Post by Tony Flury on 2011-05-02
> **unknownPoster said:**
> Pretty sure it's one of the millennium problems too.

As mentioned above  - Alan Turing proved in 1936 that the Halting problem was unsolvable. The Millenium problem I think is the NP Complete problem - which I have to be honest i have to look up everytime - because everytime i think i understand it - it gets displaced by something else.

[http://en.wikipedia.org/wiki/NP-complete](http://en.wikipedia.org/wiki/NP-complete)

---

### Post by ssam on 2011-05-02
> **kevin11951 said:**
> I have been messing around with Python for the last month or so, and I am wondering: Can Python do everything?  For example, could I take a left eye image and a right eye image and convert them to a 3D (red-blue) image using strictly Python?

edit:  I am not looking for a way to actually complete the above problem, it's just an example...

that would probably just take a few lines of code with PIL (python image library).

---

### Post by nmaster on 2011-05-02
> **cgroza said:**
> Python is not that good with image processing because it is a thing where speed matters. Languages like C++ and Java are more useful there.

this is a really good point.  a *partial* solution to this problem is to implement certain things in C/C++ and have python interface with these routines.  this is the case for numpy and scipy which are in turn used elsewhere (like opencv).  

this is still just a partial solution though.  often times, people will use interpreted languages like python for prototyping purposes and then will follow up with C/C++ when speed and performance becomes a priority.

---

### Post by brpylko on 2011-05-02
there is no programming language that can do "everything" I would describe python as "versatile" but it can have performance issues.

---

### Post by nvteighen on 2011-05-03
> **Tony Flury said:**
> It is the Halting problem - which no-one has solved - nothing to do with programming languages - it is a fundamental problem in computer science.

given an arbitrary complex program and arbitrary inputs can you by inspection prove that the program will halt.

[http://en.wikipedia.org/wiki/Halting_problem](http://en.wikipedia.org/wiki/Halting_problem)

If you read the second paragraph - you will see that a generic algorithm has been proven to be not possible

Hey, thanks for the link and the information.

---

### Post by slavik on 2011-05-03
> **brpylko said:**
> there is no programming language that can do "everything" I would describe python as "versatile" but it can have performance issues.
You are wrong.

---

### Post by |{urse on 2011-05-03
"Everything" is defined by everything that has already been done.
So yeah you could do "everything" with C++.

---

### Post by matthew.ball on 2011-05-04
> **unknownPoster said:**
> Pretty sure it's one of the millennium problems too.
Nah, that's "P = NP".

The Halting problem was well and truly solved back when everything was done on infinite tape.

They are slightly related, but the problems in P (and NP) are at least decidable, where as the halting problem is undecidable.

Edit: 
> **|{urse said:**
> "Everything" is defined by everything that has already been done.
So yeah you could do "everything" with C++.
In this context, "everything" is defined by Turing-completeness - which essentially deals with "what" is computable (see the [Church-Turing thesis]("http://en.wikipedia.org/wiki/Church%E2%80%93Turing_thesis")), this easily talks about things which haven't been done. If a language is Turing-complete (which Python is), it can compute everything that is "effectively" computable (i.e. some algorithm exists which takes some sentence from premises to a conclusion). So, while not *everything* is computable (undecidable problems for instance), in this context "everything" refers to all those problems for which there exists a decidable algorithm.

---

### Post by simeon87 on 2011-05-04
> **matthew.ball said:**
> Nah, that's "P = NP".

The Halting problem was well and truly solved back when everything was done on infinite tape.

They are slightly related, but the problems in P (and NP) are at least decidable, where as the halting problem is undecidable.

Although, the problem of whether P and NP are equal or not may be undecidable :P

---

### Post by hakermania on 2011-05-04
There is not any programming language out there that can do anything..

---

### Post by ajackson on 2011-05-04
> **NovaAesa said:**
> Correct, and in particular it's impossible in Python.
That is one of the most mucked up pieces of logic I've ever heard. If something is impossible it is impossible. If, and a big if, a solution is found who is to say that Python wouldn't be able to do it, or do it better/worse than language *X* (and vice versa).

As to your other post where you state Python can't do anything, care to explain how there are Python programs out there that DO stuff and can in fact be proven to do stuff?

Back to the original question, Python can do an awful lot of things but it isn't necessarily always the right tool for the job. Using the original example taking two images to produce a 3D image is probably doable (I've never looked at the dynamics of making 3D images but I assume it is more or less image manipulation). There is nothing to say the main program can't be in Python but actual image manipulation library written in another language (I'd advise against COBOL though :))

---

### Post by unknownPoster on 2011-05-04
> **matthew.ball said:**
> Nah, that's "P = NP".



Not exactly, I was just guessing/speculation that it may be one of them.

There are 7 Millinium Prize Problems, one of which has actually been solved. P = NP is just the most famous one.

[http://en.wikipedia.org/wiki/Millennium_Prize_Problems](http://en.wikipedia.org/wiki/Millennium_Prize_Problems)

---

### Post by matthew.ball on 2011-05-04
Yeah, but as far as complexity goes, "P = NP" is the only one (the Halting problem is a question of complexity, hence they are somewhat related).

---

### Post by NovaAesa on 2011-05-04
> **ajackson said:**
> That is one of the most mucked up pieces of logic I've ever heard. If something is impossible it is impossible. If, and a big if, a solution is found who is to say that Python wouldn't be able to do it, or do it better/worse than language *X* (and vice versa).
A solution won't be found for any problem proved to be undecidable, by definition. So your hypothetical regarding whether Python would be able to decide the problem better or worse than any other Turing complete language is irrelevant.

> 
As to your other post where you state Python can't do anything, care to explain how there are Python programs out there that DO stuff and can in fact be proven to do stuff?

Possibly I was being unclear. Yes, Python can do things (namely decide decidable problems), but it cannot do everything (namely it cannot decide undecidable problems). So the question "can Python do anything?" can be answered with "no, Python cannot do anything".

---

### Post by slavik on 2011-05-04
> **matthew.ball said:**
> Yeah, but as far as complexity goes, "P = NP" is the only one (the Halting problem is a question of complexity, hence they are somewhat related).
I think you meant to say that the halting problem is a computability problem.

---

### Post by simeon87 on 2011-05-05
> **NovaAesa said:**
> A solution won't be found for any problem proved to be undecidable, by definition. So your hypothetical regarding whether Python would be able to decide the problem better or worse than any other Turing complete language is irrelevant.

Isn't that what you were saying and what ajackson is pointing out? You were claiming there was something special about Python that made it in particular impossible. But the impossibility holds for any language, not just Python, because it's impossible for any Turing complete language.

> **NovaAesa said:**
> Correct, and in particular it's impossible in Python.

---

