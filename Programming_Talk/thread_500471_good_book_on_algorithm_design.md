---
title: "good book on algorithm design"
date: 2007-07-13
forum: Programming Talk
---

### Post by oldmanstan on 2007-07-13
apologies if this (or something similar) has been posted before, i searched and didn't find what i wanted...

i'm looking for a good, accessible book on actually designing algorithms.  i really don't care what language (if any) it uses.  i don't want it to be too intensely mathematical, i can do a reasonable amount of calculus and linear algebra but i don't want to slog through proofs and overly complex math.

i've never had any formal training in programming but i "know" several languages both scripted and compiled.  what i'm looking for i guess is a book that covers techniques and processes for designing algorithms to solve problems, how to use a programming language effectively.

again, math is fine but i'm not looking for a "math book".

honestly i'm not even sure that such a thing exists, a search of amazon yielded little and the books i've found elsewhere have been focused on specific mathematical issues.

anyway, suggestions would be appreciated...

---

### Post by xtacocorex on 2007-07-13
A study of mathematics and how to solve those problems is analogous to algorithm design IMO. 

Say you have to write a code to capture 1D shocks using Euler.  I would research the method and how it is solved by hand or numerically just to mimic it in code.  

I learned to program for numerical methods, so to me that's the only type of programming.  (I know it isn't, but I don't usually code anything besides stuff involving lots of math)

---

### Post by llanitedave on 2007-07-14
Not algorithms for solving specific narrow problems, but as the title suggests [Design Patterns: Elements of Reusable Object-Oriented Software]("http://www.amazon.com/Design-Patterns-Object-Oriented-Addison-Wesley-Professional/dp/0201633612").  I found my copy, oddly enough, in pristine condition, under a pine tree twenty feet off of a dirt road in a remote mountain valley.  If that's not karma, I don't know what is.  

It's not language specific.

---

### Post by Wybiral on 2007-07-14
> **llanitedave said:**
> I found my copy, oddly enough, in pristine condition, under a pine tree twenty feet off of a dirt road in a remote mountain valley.

That's pretty awesome.

---

### Post by xtacocorex on 2007-07-14
> **llanitedave said:**
> I found my copy, oddly enough, in pristine condition, under a pine tree twenty feet off of a dirt road in a remote mountain valley. 
Are you sure the book is real? :)

---

### Post by pmasiar on 2007-07-14
Design-Patterns is good, but it applies mostly to C++/Java class of languages (statically typed). In dynamically typed languages so tricks are trivial or unnecessary. Functional languages have rather different approaches, too. 

It is hard to write good cross-language book. Unfortunately, programming art is not advanced enough (or too advanced). Different languages are designed/optimized for different classes of problems, and solving problems outside of target area is clumsy (or at least look clumsy in code). So IMHO you are better off deciding which language to learn first.

Because you are street fighter, IMHO you may consider to go for rapid app development languages (big companies using "big" languages like Java and C++ will have hard time to overlook your lack of formal degrees and certifications). Python + TurboGears + AJAX, learn to build web sites in weeks instead of months.

OK, now direct answer to your question: :-)
[here](http://learnpython.pbwiki.com/#DataStructures) in my wiki are couple of links to "algorithms only" books. You can also look around wikibooks and may find some more.

---

### Post by the_unforgiven on 2007-07-14
Slightly off-topic, but I suggest you read this:
[http://extreme.infomagic.net/static/knuth_turingaward.pdf](http://extreme.infomagic.net/static/knuth_turingaward.pdf)

It's the speech delivered by [Donald Knuth]("http://en.wikipedia.org/wiki/Donald_Knuth") when he received ACM Turing Award in 1974. It revolves around the idea "Computer Programming as Art".

It's quite interesting and helpful ;)

Now, as for the algorithm books, this one is a standard book:
[http://en.wikipedia.org/wiki/Introduction_to_Algorithms](http://en.wikipedia.org/wiki/Introduction_to_Algorithms)

---

### Post by hod139 on 2007-07-14
> **the_unforgiven said:**
> 
Now, as for the algorithm books, this one is a standard book:
[http://en.wikipedia.org/wiki/Introduction_to_Algorithms](http://en.wikipedia.org/wiki/Introduction_to_Algorithms)


The CLRS book is very good and I also recommend it.  It uses pseudocode for all the algorithms so your first requirement is satisfied.  However, this book is fairly heavy in the math, mostly discrete math and graph theory.  But, as pointed out by xtacocorex, any good algorithms book will be heavy in the math.  This is because algorithm design in computer science is interested in describing how fast/good and algorithm is, and how to design good algorithms.  This analysis requires a bit of math.

---

### Post by earobinson on 2007-07-14
Jon Kleinberg and Éva Tardos: Algorithm Design (2006) by Pearson Education, ISBN: 0-321-29535-8
Cormen, Leiserson, Rivest, Stein: Introduction to Algorithm (2nd edition) McGraw-Hill (2001), ISBN: 0-07-013151-1

---

### Post by oldmanstan on 2007-07-14
thank you all!

 i will have to sift through the recommendations to see which one(s) work for me.

---

### Post by Mirrorball on 2007-07-14
I also recommend Cormen's book, but it is certainly a "math book."

---

### Post by Houman on 2007-07-15
how about the classics by Donald Knuth?

the The Art of Computer Programming series is probably one of the best known works in this subject;

Houman

---

### Post by Mathiasdm on 2007-07-15
[Algorithms in C++](http://www.amazon.com/Algorithms-Parts-1-4-Fundamentals-Structure/dp/0201350882) is the one I've used to study algorithms. It's a great book. I'm thinking about buying the second one too.

And I know, it says 'in C++', but these are algorithms that you can change yourself, and use in other languages.

---

### Post by the_unforgiven on 2007-07-15
> **Houman said:**
> how about the classics by Donald Knuth?

the The Art of Computer Programming series is probably one of the best known works in this subject;

Houman
Yes, but it's heavily influenced by mathematics - and the primary requirement of the OP was "less math" ;)
That is why I did not bother recommending it.

---

### Post by grado on 2007-07-15
Stan, the book you are looking for might be the one by Kleinberg and Tardos
[http://www.aw-bc.com/info/kleinberg/](http://www.aw-bc.com/info/kleinberg/)

While Corman and Knuth are timless, this is considered easy to follow.

---

### Post by oldmanstan on 2007-07-16
> **grado said:**
> Stan, the book you are looking for might be the one by Kleinberg and Tardos
[http://www.aw-bc.com/info/kleinberg/](http://www.aw-bc.com/info/kleinberg/)

While Corman and Knuth are timless, this is considered easy to follow.

based on the description that one does look interesting, perhaps even in conjunction with one of the others...

also, to some of the other helpful posters (thank you btw) i realize i did specify that i didn't want it to be too "mathy" but i also recognize that in the end the math is necessary.  i just want to dip my toe in for a bit and get a feel for the material before i dive in head first :)

so to that effect, all suggestions are helpful, even more intense ones...

see, i tried searching the online catalog at my library but very little comes up for "algorithms", even searching the whole system (basically every uni. library in illinois)... i mean, i get tons of results but they're impossible to sift through since the catalog info doesn't generally include a synopsis unless the book was published very recently

in any event, thanks for all the suggestions, i have to start checking some of these out this week and sifting to pick one to read through

---

### Post by earobinson on 2007-07-16
let us know what you pick!

---

### Post by oldmanstan on 2007-07-23
so far i've gotten a chance to look at 2 of the suggested books...

design patterns - the first 2 chapters were very interesting, i learned some things about oop that hadn't crossed my mind previously.  the actual "patterns" though are sort of beyond me at this point though.  i guess they're too practical for lack of a better word :)

algorithms in c++ - this one has me interested, the first chapter dives right into designing an actual algorithm (albeit a pretty simple one) and rather than just presenting the "best" way to solve the problem it steps you through the whole process of arriving at a method that will satisfy demanding requirements.  this is useful because i'm getting more of a feel for how things are actually done without being too practical (business-ish hehe).  it seems more abstract than the design patterns book so i think i'm going to muddle through the rest of it.

thanks everyone who made suggestions!

---

