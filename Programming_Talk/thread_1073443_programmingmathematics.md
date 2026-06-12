---
title: "programming/mathematics"
date: 2009-02-18
forum: Programming Talk
---

### Post by badperson on 2009-02-18
Hi,
I got into programming kind of late, and have not done any math at all since high school, and I completely SUCK at it...so I'm going thru a book; really remedial stuff; fractions and so forth, but I'm enjoying it and want to keep it up. I figure if I stay regular I can work my way thru algebra and geometry this year, and then maybe get into some basic calculus. 

I'd like to get my math skills good enough to not be utterly bewildered by the knuth books, and was wondering if any one had some ideas as to what the most important kind of math for prgramming is. 
thanks,
bp

---

### Post by kavon89 on 2009-02-18
Algebra and Calculus imo

---

### Post by Cracauer on 2009-02-18
You need some sense of statistics, be comfortable with probabilities, to do any kind of high-performance computing (or non-suck performance computing for that matter).

---

### Post by howlingmadhowie on 2009-02-18
i'd say just enjoy yourself learning maths. maybe you could write programs to elucidate the maths you're learning. this will start to get interesting when you get to taylor series and later fourier analysis. 

once you've got basic calculus learnt, i'd recommend a book like

mary boas: mathematical methods in the physical sciences.

it's a bit informal compared with maths books on numeric, but it's very easy to learn from.

---

### Post by aszxcv on 2009-02-18
discrete math
linear algebra

---

### Post by PythonPower on 2009-02-18
Algorithmics, computational complexities, matrix math, chromatic polynomials, Stern-Brocot trees, continued fractions, inclusion-exclusion principle, Boolean algebra... Those come up most (for me!), but just about all math can be useful.

---

### Post by Zugzwang on 2009-02-18
To sum it up: **All** math is useful but what you really need depends on what you are specializing in.

---

### Post by CptPicard on 2009-02-18
I get the feeling that the OP is given way too a complex answer if the original question is simply what sort of math is related to programming... 

The basics are really simple discrete math, naive set theory, logic, and a little bit of number theory. That's it. Calculus in particular deals with continuous quantities, so you rarely see it in (fundamental) computing. It does turn up in a lot of application domains of course.

Now, the things you actually program tend to introduce you to mathematics and make you use it, so that's why programming is a nice math teaching tool. You can get started with little, but you can learn much (for example linear algebra if you do graphics).

The Knuth books are overrated... the guy is able to spend a lot of pages on fundamentally fairly simple stuff. I never could see what the fuss about them is all about, and I actually like the theory side.

---

### Post by badperson on 2009-02-18
thanks for the replies...all good suggestions, the long and short of it is...keep working. 

anyway, I was wondering, now that I'm forcing myself to redo all these kiddie little math exercises, I was wondering, when you have this in java: 

```
int sum = (111-67);
```
how does it do that calculation? Is it in assembly? Is there some point where it breaks the number into individual digits and say, "7 is greater than one, therefore make 1 11, make the preceding one a zero, 11 - 7 is four...etc. 

thanks, 
bp

---

### Post by simeon87 on 2009-02-18
> **badperson said:**
> thanks for the replies...all good suggestions, the long and short of it is...keep working. 

anyway, I was wondering, now that I'm forcing myself to redo all these kiddie little math exercises, I was wondering, when you have this in java: 

```
int sum = (111-67);
```
how does it do that calculation? Is it in assembly? Is there some point where it breaks the number into individual digits and say, "7 is greater than one, therefore make 1 11, make the preceding one a zero, 11 - 7 is four...etc. 

thanks, 
bp

In Java, the code is compiled to bytecode - the details of this file format can be found on the web. But it doesn't 'read' the source code like you said, it's compiled to instructions, like ADD, MULT, PUSH, POP (for the stack that it uses to perform the computation) etc.

Edit: well, I should add that in order to compile to bytecode, it does have to read the source code of course..

---

### Post by CptPicard on 2009-02-18
> **badperson said:**
> 
```
int sum = (111-67);
```
how does it do that calculation? Is it in assembly?

It gets compiled into a Java bytecode instruction, which then gets JIT-compiled into the CPU-specific instruction. Now, how that is actually implemented is an engineering exercise...

---

### Post by kavon89 on 2009-02-18
> **badperson said:**
> thanks for the replies...all good suggestions, the long and short of it is...keep working. 

anyway, I was wondering, now that I'm forcing myself to redo all these kiddie little math exercises, I was wondering, when you have this in java: 

```
int sum = (111-67);
```
how does it do that calculation? Is it in assembly? Is there some point where it breaks the number into individual digits and say, "7 is greater than one, therefore make 1 11, make the preceding one a zero, 11 - 7 is four...etc. 

thanks, 
bp

in binary, see [Two's Compliment]("http://en.wikipedia.org/wiki/Two%27s_complement") for more info:

(subtraction)
110 1111 == 111
100 0011 == 67
_______________
010 1100 == 44

---

### Post by nvteighen on 2009-02-18
> **badperson said:**
> t
```
int sum = (111-67);
```
how does it do that calculation? Is it in assembly? Is there some point where it breaks the number into individual digits and say, "7 is greater than one, therefore make 1 11, make the preceding one a zero, 11 - 7 is four...etc. 


Three words: You don't care :)

...as long as it does what you do. That's the reason why we don't use Assembly and why you "trust" Java to do that operation correctly. However it does it is only relevant for the Java developers and engineers developing computers, not actually programmers (or better said, it's not a programming problem in itself although it may be relevant in some kind of programming).

Maths? Well, in general terms you need Linear Algebra, Logic, Set Theory and basic Algorithms. Then, if you e.g. go into gaming, you'll need lots of complex Geometry (Vectorial, Trig, Calculus, whatever). If you need high-optimizations, then you have to move further in Algorithms... So, besides that basic stuff I said, I think the rest depends on what you're doing.

---

### Post by wmcbrine on 2009-02-18
> **badperson said:**
> ```
int sum = (111-67);
```
how does it do that calculation? Is it in assembly? Is there some point where it breaks the number into individual digits and say, "7 is greater than one, therefore make 1 11, make the preceding one a zero, 11 - 7 is four...etc.Internally, computers use binary numbers. Decimal representation is only for the convenience of humans. So the first step for the compiler, on encountering those numbers in the source code, would be to convert them to their binary representations.

Modern computers represent negative numbers using two's complement. To take the two's complement of a number, you invert each bit, and then add one. So, to do a subtraction, you take the two's complement of the second number, and add that to the first number.

In this example, because the result is fixed, the calculation would be performed at compile time, and only the binary value of the result (44) would be stored into the bytecode.

I'm glossing over a lot here, in an attempt to avoid adding to your confusion. :)

---

### Post by kjohansen on 2009-02-18
Linear algebra is involved in a lot of things.

A paraphrase from the first page of one my linear algebra books "if a math problem can be solved it can be stated in terms of linear algebra"

I beleive it was a book by Gilbert Strang at MIT...

---

### Post by howlingmadhowie on 2009-02-19
> **badperson said:**
> thanks for the replies...all good suggestions, the long and short of it is...keep working. 

anyway, I was wondering, now that I'm forcing myself to redo all these kiddie little math exercises, I was wondering, when you have this in java: 

```
int sum = (111-67);
```
how does it do that calculation? Is it in assembly? Is there some point where it breaks the number into individual digits and say, "7 is greater than one, therefore make 1 11, make the preceding one a zero, 11 - 7 is four...etc. 

thanks, 
bp

have a look here: [Cmos]("http://en.wikipedia.org/wiki/Cmos")
and then here: [Adder]("http://en.wikipedia.org/wiki/Full_adder#Full_adder")
reading this could also prove useful: [Two's complement]("http://en.wikipedia.org/wiki/Twos_complement")
At which point you're pretty much ready to start learning machine code :)

---

### Post by howlingmadhowie on 2009-02-19
> **CptPicard said:**
> It gets compiled into a Java bytecode instruction, which then gets JIT-compiled into the CPU-specific instruction. Now, how that is actually implemented is an engineering exercise...

oh i get it. that's why i always get annoyed with mathematicians. as someone who spent his childhood playing with technic lego, i'm fascinated by the engineering and the maths i find pretty boring. that's not quite true. maths can be beautiful but it reminds me of what brahms (?) said about music theory, something like "it's like describing a sumptuous banquet but not allowing anybody to taste it" (i can't find the quote on google, so i've obviously mangled it beyond recognition, but the basic idea is the same).

---

### Post by PythonPower on 2009-02-19
> oh i get it. that's why i always get annoyed with mathematicians. as someone who spent his childhood playing with technic lego, i'm fascinated by the engineering and the maths i find pretty boring. that's not quite true. maths can be beautiful but it reminds me of what brahms (?) said about music theory, something like "it's like describing a sumptuous banquet but not allowing anybody to taste it" (i can't find the quote on google, so i've obviously mangled it beyond recognition, but the basic idea is the same).

Math is not just theoretical. It can be extremely practical but then loses its "absolute truth". Math in about the only subject which allows proof.

---

### Post by howlingmadhowie on 2009-02-19
> **PythonPower said:**
> Math is not just theoretical. It can be extremely practical but then loses its "absolute truth". Math in about the only subject which allows proof.

i'm going to get picky here.

maths is not and cannot be practical. the applications of maths may be practical, but you can't build anything out of maths, not like you can build things out of lego. many subjects allow proof, it's just that the definition of what constitutes a proof depends on the subject. with maths you have the idea of the axiom and allowed manipulations. in law, for example, the idea of proof is very different. 

now i'll stop being picky, because i know what you meant :)

---

### Post by PythonPower on 2009-02-19
You're right and it's a distinction I often make when criticising the inclusion of applied topics into mathematical syllabi... In this case, I was using the term very loosely. Nowadays, topics like Statistics and Mechanics are often called math too.

---

### Post by CptPicard on 2009-02-19
Hmm... any field that acts rationally using logic allows for proof. Mathematics is just study of abstract concepts' properties and relationships using logic.

I have always found mathematics quite practical -- actually it is at its best IMO when a mathematical/theoretical reasoning comes into a practical result all by itself (consider theoretical physics...). It affirms, in a way, that "the world makes sense" :)

---

### Post by nvteighen on 2009-02-19
> **CptPicard said:**
> Hmm... any field that acts rationally using logic allows for proof. Mathematics is just study of abstract concepts' properties and relationships using logic.

I have always found mathematics quite practical -- actually it is at its best IMO when a mathematical/theoretical reasoning comes into a practical result all by itself (consider theoretical physics...). It affirms, in a way, that "the world makes sense" :)
Maths is actually logic applied to quantities. These quantities can refer to different things, but the key point is always that you're measuring "how much" something is according to some parameter.

---

### Post by OfAllTime on 2009-02-19
What would the name be for the field of math that includes two's complement?

Thanks,
Johnny

---

### Post by PythonPower on 2009-02-19
[QUOTE=nvteighen]Maths is actually logic applied to quantities. These quantities can refer to different things, but the key point is always that you're measuring "how much" something is according to some parameter.[/QUOTE]

Math is just a set of axioms and logic.

[QUOTE= OfAllTime]What would the name be for the field of math that includes two's complement?[/QUOTE]

Combinatorics/ arithmetic if anything... But two's complement is a standard rather than having some inherent reasoning behind it (from the mathematical sense - it makes sense to humans).

---

### Post by kavon89 on 2009-02-19
> **OfAllTime said:**
> What would the name be for the field of math that includes two's complement?

Thanks,
Johnny

Computer Science

---

### Post by nvteighen on 2009-02-19
> **PythonPower said:**
> Math is just a set of axioms and logic.

Of course it is, but formed by a special kind of axioms: those that refer to quantity.

---

### Post by s.fox on 2009-02-19
I think Algebra is very important, as well as a firm understanding of basic pure math principles.

---

### Post by CptPicard on 2009-02-19
> **OfAllTime said:**
> What would the name be for the field of math that includes two's complement?

Number theory, algebra.

> **nvteighen said:**
> Of course it is, but formed by a special kind of axioms: those that refer to quantity.

I am not all that sure of that... quantity already assumes number-theoretic abstractions and things derived from them. Consider something like topology, formal logic or even just abstract algebra... there is a lot of non-quantity stuff in mathematics. I think that definition of "properties and relationships of abstract concepts" was some sort of actual more official definition I picked up somewhere.

---

### Post by Reiger on 2009-02-20
Why ask what Math is, when you can ask what it _means_ ?

Math a short for Mathematics which is English for Mathematika (Greek) or "that which can be learned/understood/precisely known". So to sum up: Math <=> everything. At least since the moment people started messing with categories, relations and whathaveyou.

---

### Post by nvteighen on 2009-02-20
> **CptPicard said:**
> 
I am not all that sure of that... quantity already assumes number-theoretic abstractions and things derived from them. Consider something like topology, formal logic or even just abstract algebra... there is a lot of non-quantity stuff in mathematics. I think that definition of "properties and relationships of abstract concepts" was some sort of actual more official definition I picked up somewhere.

It's all about quantities; that definition of yours, IMO, is better applied to logics than to maths. In formal logics, you just deal with the "form" of things and that's why you can make general conclusions that serve for whatever you put inside that "form". But abstract algebra always assumes that whatever you're dealing with is some kind of quantity.

> **Reiger said:**
> Why ask what Math is, when you can ask what it _means_ ?

Math a short for Mathematics which is English for Mathematika (Greek) or "that which can be learned/understood/precisely known". So to sum up: Math <=> everything. At least since the moment people started messing with categories, relations and whathaveyou.

That's what in Linguistics is called **Etymological Fallacy**. You can't conclude the meaning of a word by looking at what its primitive components meant, specially when you're changing from one linguistical system (Greek) to another completely different (English).

But anyway, to clean the etymology a bit :): From the verb *manthánein* "to learn" (root: *math-*, as the Aorist tense is *émathon*) you get the verbal noun *máthema* "lesson" (stem *mathemat-*). "Mathematics" is derived from *mathematiké* by using the adjectival suffix *-ik-*, so we can assume it's actually a shortening of the phrase *mathematiké <téchne>* (< > in Linguistics means an hypothetical addition) "the mathematical art/technique". As far as I know, it already meant specifically Mathematics in Classic Greek.

But you just can't conclude that Maths = any rational knowledge from there. Words mean what people make it mean... and today Maths is referred to a certain kind of knowledge.

Otherwise, you should say everything is Philosophy as any knowledge is an act of "Interest/love to knowledge" as Greeks thought. (Euclides, Pythagoras, Thales, etc. all considered themselves and were called "philosophers", not "mathematicians"... and Plato taught Geometry)

---

### Post by CptPicard on 2009-02-20
> **nvteighen said:**
> But abstract algebra always assumes that whatever you're dealing with is some kind of quantity.

No it doesn't. :) It assumes you've got some set, and then some operator or operators on that set. Then you try to figure out what sort of properties that combination of set plus operator(s) over the set has. And turns out you get groups, rings... you deal with quantities only in the special corner case of "sets of numbers", which of course originally motivated the study of algebra, of course.

By the way, I was thinking the other day that the reason why I find functional programming so appealing is that it has nice algebraic qualities to it. You declare entities and then define "operators" on those entities, which in turn produce other new entities. In particular, functional programming allows you to be very flexible in your operator definition and the way you *combine* operators to produce new ones. It really is the very meaningful operator "words" that are the neat thing. Lisp's macro system just adds to that by being the ultimate syntactic sugar on top of the functional word-building machinery.


> 
That's what in Linguistics is called **Etymological Fallacy**. ...

That'll teach him not to mess with a linguist (ics student) ;)

---

### Post by nvteighen on 2009-02-20
> **CptPicard said:**
> No it doesn't. :) It assumes you've got some set, and then some operator or operators on that set. Then you try to figure out what sort of properties that combination of set plus operator(s) over the set has. And turns out you get groups, rings... you deal with quantities only in the special corner case of "sets of numbers", which of course originally motivated the study of algebra, of course.

Hm... I sorta see your point. But those sets, aren't generated by quantities of some kind? Maybe I'm not being clear on what I'm referring to by "quantity": instead of looking at what something **is** (quality) but what is its **value** according to some metric you define.

> 
By the way, I was thinking the other day that the reason why I find functional programming so appealing is that it has nice algebraic qualities to it. You declare entities and then define "operators" on those entities, which in turn produce other new entities. In particular, functional programming allows you to be very flexible in your operator definition and the way you *combine* operators to produce new ones. It really is the very meaningful operator "words" that are the neat thing. Lisp's macro system just adds to that by being the ultimate syntactic sugar on top of the functional word-building machinery.

And considering Lisp's syntax, the thing is much more extreme as you can't (and don't need to) distinguish between functions and operators not even at a syntactic level.

---

### Post by CptPicard on 2009-02-20
> **nvteighen said:**
> Hm... I sorta see your point. But those sets, aren't generated by quantities of some kind?

No, they are not. They are generated by some sort of conditions that are able to distinguish what is in the set and what is not. Of course, the very definition of what a set is has been a major headache in mathematics -- naive set theory seems obvious, but is vulnerable to Russell's paradox (look it up, it's a remarkable insight that almost torpedoed mathematics). Axiomatic set theory on the other hand is much more complex but more robust :)

> 
 Maybe I'm not being clear on what I'm referring to by "quantity": instead of looking at what something **is** (quality) but what is its **value** according to some metric you define.

Here I must be a stickler to detail when the detail really is very important -- a "metric" on a set is a very well defined concept so it must not be abused. When we're talking of continuous sets, the concept of metric is crucial for modern theory of integrals; and when you're talking of discrete sets, a metric can be seen as the cardinality (number of members) of the set. A related concept is countability of the set -- a set can be infinite, yet countable (see Cantor). Only after working through details like these can we be on a reasonably solid foundation to even try tackling things like the concept of number and question of quantities, measured by function from set to some member of some number class. To say that mathematics just deals with quantities is very wrong and "naive" -- a lot of "modern" math actually has been about disabusing ourselves of that notion!

> And considering Lisp's syntax, the thing is much more extreme as you can't (and don't need to) distinguish between functions and operators not even at a syntactic level.

It really is fascinating to see the relationship of "syntactic sugar" vs. fundamental language constructs as expressed in Lisp. I mean, Lisp has a full front-end Turing-complete compiler on the non-evaluated symbols as a first pass, so you can implement anything already in terms of macros, but the fundamental "engine" of the language contains the minimum amount of maximum performance language elements so that the balance is optimal. And yet I feel like I am left wanting of SOME things, such as explicit continuations and true lazy lists / generators (which could be implemented in macros as continuations). 

There are macro-compilers for continuations -- full-blown CPS transformers for blocks of code -- but the fact remains that you need to explicitly use that stuff -- it's not available on demand everywhere.

And to think some people think Lisp is appreciated for the same reason LOLCODE is...

---

### Post by nvteighen on 2009-02-20
> **CptPicard said:**
> No, they are not. They are generated by some sort of conditions that are able to distinguish what is in the set and what is not. Of course, the very definition of what a set is has been a major headache in mathematics -- naive set theory seems obvious, but is vulnerable to Russell's paradox (look it up, it's a remarkable insight that almost torpedoed mathematics). Axiomatic set theory on the other hand is much more complex but more robust :)

Ok, Russell's paradox gave me the clue. The definition of a set is actually outside the set and it's not part of itself... otherwise we get into the Russell's paradox. :) Thanks!

> 
Here I must be a stickler to detail when the detail really is very important -- a "metric" on a set is a very well defined concept so it must not be abused. When we're talking of continuous sets, the concept of metric is crucial for modern theory of integrals; and when you're talking of discrete sets, a metric can be seen as the cardinality (number of members) of the set. A related concept is countability of the set -- a set can be infinite, yet countable (see Cantor). Only after working through details like these can we be on a reasonably solid foundation to even try tackling things like the concept of number and question of quantities, measured by function from set to some member of some number class. To say that mathematics just deals with quantities is very wrong and "naive" -- a lot of "modern" math actually has been about disabusing ourselves of that notion!

Ok. I guess I shouldn't mess with a Maths-guy... ;)

---

### Post by PythonPower on 2009-02-20
[QUOTE=nvteighen]Of course it is, but formed by a special kind of axioms: those that refer to quantity.[/QUOTE]

But not just quantity (although mainly). Boolean algebra doesn't have quantities and many theorems are on structure too.

---

### Post by CptPicard on 2009-02-20
> **nvteighen said:**
> Ok, Russell's paradox gave me the clue. The definition of a set is actually outside the set and it's not part of itself... otherwise we get into the Russell's paradox.

Interestingly, Russell's paradox foreshadows Turing's incomputability-proofs -- the form is analogous. There is something very deep there :)

---

### Post by jpkotta on 2009-02-20
Interesting thread.

My definition of math is the study of patterns.  I have a wonderful quote about that:
[QUOTE=Lynn A. Steen]
Mathematics is the science of patterns.  The mathematician seeks patterns in number, in space, in science, in computers, and in imagination.  Mathematical theories explain the relations among patterns; functions and maps, operators and morphisms bind one type of pattern to another to yield lasting mathematical structures.  Applications of mathematics use these patterns to *explain* and predict natural phenomena that fit the patterns.  Patterns suggest other patterns, often yielding patterns of patterns.  In this way mathematics follows its own logic, beginning with patterns from science and completing the portrait by adding all patterns that derive from initial ones.
[/QUOTE]

But back OT, math teaches a mindset and a way of thinking that is essential to programming well.  It's almost irrelevant what branch of math you learn; almost all of them have the essential ideas of reductionism and logical connections.  Math also tends to favor the simplest, most elegant solution, which is usually the right one for a program.  Finally, a strong theme in math is to transform one type of problem into an equivalent, easier problem, which is clearly useful for programming.

---

