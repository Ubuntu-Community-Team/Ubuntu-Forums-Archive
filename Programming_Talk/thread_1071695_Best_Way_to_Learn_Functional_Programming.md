---
title: "Best Way to Learn Functional Programming?"
date: 2009-02-16
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-02-16
What language would best break my imperative mindset?  Also, what should i program with the chosen language (i hate math challenges)

---

### Post by mriedel on 2009-02-16
Scheme and Prolog are often used to teach the declarative paradigm in academic environments.

The best thing to do with a functional language you're trying to learn is, of course, something that fits the nature of the functional paradigm. Basically anything excessively recursive. Do anything where you traverse lists or graphs.

Make a recursive definition for a graph (a graph node is a list of graph nodes or null), then implement a function that finds a route (or list of routes) from one given node to another.

Or were you looking for something more complex / real world applicable? The problem with functional languages is that interfacing your logic is harder. You might want to look into how to integrate [your functional language of choice] with [your imperative language of choice].

---

### Post by Reiger on 2009-02-16
I thought Prolog was more the declarative sort of programming, well suited to solve problems given a set of constraints and some input? [http://en.wikipedia.org/wiki/Prolog](http://en.wikipedia.org/wiki/Prolog)

Anyways, if you want a pure functional language (which will pretty much force you to re-evaluate your imperative coding strategies) Haskell and friends would be a fine choice.

---

### Post by sarang on 2009-02-16
I _highly_ recommend scheme and haskell. Python is not bad either.

Scheme was the language of choice for Massachusetts Institute of Technology's highly acclaimed 'Structure and Interpretation of Computer Programs' functional programming class (6.001). The class was aimed at students with negligible functional programming experience. The text used was [http://mitpress.mit.edu/sicp/full-text/book/book.html](http://mitpress.mit.edu/sicp/full-text/book/book.html) and the recommended programming environment was 'DrScheme' from [http://www.plt-scheme.org/](http://www.plt-scheme.org/)
After gaining sufficient familiarity with DrScheme, I recommend moving to MIT-Scheme, a scheme dialect more powerful than the one used by DrScheme.


What to program (change the year in the url for more):
[http://sicp.ai.mit.edu/Spring-2007/](http://sicp.ai.mit.edu/Spring-2007/)
[http://sicp.ai.mit.edu/Fall-2007/](http://sicp.ai.mit.edu/Fall-2007/)
Assignments:
[http://sicp.ai.mit.edu/Spring-2007/projects/index.html](http://sicp.ai.mit.edu/Spring-2007/projects/index.html)
[http://sicp.ai.mit.edu/Fall-2007/projects/index.html](http://sicp.ai.mit.edu/Fall-2007/projects/index.html)

---

### Post by mriedel on 2009-02-16
> **Reiger said:**
> I thought Prolog was more the declarative sort of programming, well suited to solve problems given a set of constraints and some input? [http://en.wikipedia.org/wiki/Prolog](http://en.wikipedia.org/wiki/Prolog)

Indeed, Prolog follows the constraint programming paradigm, while scheme is functional. Both are declarative though, which I was considering the point here, as the author said they wanted to get away from the imperative paradigm. I was wrong to say Prolog was functional.

The way functions work in Scheme in Prolog are quite the same though. Both are recursive languages.

Anyway if you want to go for something truly and purely functional (as opposed to just any recursive language), by all means start with Scheme. It'll make you end up with a fetish for parentheses, but it's a good start and easy to learn.

---

### Post by Wybiral on 2009-02-16
> **mriedel said:**
> Anyway if you want to go for something truly and purely functional (as opposed to just any recursive language), by all means start with Scheme. It'll make you end up with a fetish for parentheses, but it's a good start and easy to learn.

If you're going for _purely_ functional, haskell seems like the most applicable. Scheme can be functional, but it doesn't necessarily encourage it in all situations... Haskell requires it.

I'd rather have a parenthetical fetish than a semicolon / squiggly-brace fetish :p

---

### Post by CptPicard on 2009-02-16
In Prolog, they're predicates, not functions :) And you can ask Prolog to satisfy any "holes" in the predicates that you're not filling in.

And as far as recursion goes... all Turing-complete languages need to be able to handle recursive structure in some way. Functional-programming languages just tend to just make it very explicit that loops are just syntactic sugar for tail-recursion :)

---

### Post by Reiger on 2009-02-16
Well to a certain extent: predicates are just that: functions! Ooh the joy of normalizing predicates, see all the functions pop up... :p

---

### Post by jimi_hendrix on 2009-02-16
well i already know scheme so it seems like the logical place to start.  but i don know what to *do* with it...and also my scheme ends up looking like C with recursion (set! foo (read))

---

### Post by Phenax on 2009-02-16
Haskell

---

### Post by CptPicard on 2009-02-16
> **Reiger said:**
> Well to a certain extent: predicates are just that: functions!

Sure, with the exception that in Prolog you aren't interested in the "return value" but expect it to be true... and then just mess with the parameters to "make it so" (I love that expression...). Which, of course, you know, but just for the interested other readers :p


> **jimi_hendrix said:**
> but i don know what to *do* with it...and also my scheme ends up looking like C with recursion (set! foo (read))

Well, start by doing something like messing with lists... implement functional-style stacks, list merges, member searches, reversions...

---

### Post by jimi_hendrix on 2009-02-16
sounds minorly fun

---

### Post by mriedel on 2009-02-16
> **Wybiral said:**
> If you're going for _purely_ functional, haskell seems like the most applicable. Scheme can be functional, but it doesn't necessarily encourage it in all situations... Haskell requires it.

I'd rather have a parenthetical fetish than a semicolon / squiggly-brace fetish :p

"by all means start with Scheme" was directed at my previous Scheme or Prolog statement. I wasn't saying Scheme > Haskell for learning functional programming.

[quote=jimi_hendrix]sounds minorly fun[/quote]

Writing real world applications in a functional language isn't easy. Those languages are mostly used for very specific purposes or in conjunction with imperative languages. If you'd like to write something that actually does something, consider Python. It supports both the functional and the imperative paradigm, so that mixing the two becomes very easy.

---

### Post by nvteighen on 2009-02-17
> **jimi_hendrix said:**
> well i already know scheme so it seems like the logical place to start.  but i don know what to *do* with it...and also my scheme ends up looking like C with recursion (set! foo (read))

Look at the SICP videos: [http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/](http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/)

Almost no set!s except in the discussion about imperative paradigm!

---

### Post by howlingmadhowie on 2009-02-17
good functional languages? 

smalltalk, ruby, scheme and lisp, javascript

python is not a good example because it has poor support for lambda calculus:

in python:
```

>>> def add(n):
...  return lambda x: n+x
...
>>> add3=add(3)
>>> add3(5)
8
>>>

```
and there's no way to have the lambda extend over more than one line.

meanwhile in javascript (in firebug):
```

>>> add = function (n) { return function (x) { return n+x; }; }
function()
>>> add3=add(3)
function()
>>> add3(5)
8

```

or in scheme of course:
```

guile> (define add
        (lambda (x) (lambda (n) (+ n x))))
guile> (define add3 (add 3))
guile> (add3 5)
8
guile> 

```

---

### Post by matthew.ball on 2009-02-17
Hah, I like it "best way to learn functional programming?" - "learn the lambda calculus"

Though, I would also add mathematical/structural induction.

---

### Post by Reiger on 2009-02-17
> **jimi_hendrix said:**
> sounds minorly fun

More fun, less instructive: try writing Mastermind.

Of course the typical functional programming excersises involve _computing_ stuff. Like primes, fibonacci sub-sequences etc. etc.

---

### Post by sarang on 2009-02-17
For a 'real-world' example:
[http://www.paulgraham.com/avg.html](http://www.paulgraham.com/avg.html)

---

### Post by Gordon Bennett on 2009-02-17
Binary gate logic, because it all comes down to it.

*cough*

---

### Post by howlingmadhowie on 2009-02-18
> **Gordon Bennett said:**
> Binary gate logic, because it all comes down to it.

*cough*

that depends upon how you look at programming. 

the mathematician would say that the computer is to programming what the telescope is to astronomy or what the test tube is to chemistry. 

the other extreme is to say that a programming language is a way to combine certain commonly used state changes in nand-gates.

---

### Post by CptPicard on 2009-02-18
> **howlingmadhowie said:**
> 
the other extreme is to say that a programming language is a way to combine certain commonly used state changes in nand-gates.

Combinations of logic gates just happen to be a convenient physical manifestation of a Turing-complete language... :) (yes I am in the first camp :) )

It's interesting to see how even in the basic theoretical models of computation -- Turing machine vs. lambda calculus -- you see the engineering vs. mathematics distinction... the latter does not need the concept of state at all, which is why it is easier to prove a lot of stuff in LC in comparison to TMs. LC also gives you a lot of things "for free" that would be totally non-obvious in TMs (thinking of currying, closures..) 

Of course this goes the other way around in a lot of cases... for counting you need to do Church numerals etc.. :) but that's why you can use (proven correct) extensions to LC. These can become functional programming languages.

---

### Post by howlingmadhowie on 2009-02-18
> **CptPicard said:**
> Combinations of logic gates just happen to be a convenient physical manifestation of a Turing-complete language... :) (yes I am in the first camp :) )

i never quite understood why the turing machine is still so popular in computer science degrees. i can't see why it's of more than historical value, but profs still like to use it. i can understand spending time on deriving the minimal set of functionalities and properties a machine must have to be turing complete, but the turing machine itself is just a turing tarpit and it would be enough to have seen it once. what do you think?

---

### Post by CptPicard on 2009-02-18
Well, I guess the value of the TM is indeed that it can be seen as a "machine" and the basic operations are "obvious", so that you can then build from there and really see you're dealing with *mechanical* computation all the way. Of course the most important idea relating to TMs is the Universal Turing Machine... it really gave us the stored program idea.

You are right in thinking that it's enough to "have seen it once" in a way... most of the important proofs don't actually construct machines -- they just assume them and then produce counter-examples or something. You could just as well substitute the machine for "algorithm".

---

### Post by matthew.ball on 2009-02-18
Haskell (at least what I know before monads become involved), is pretty much a direct implementation of structural induction.

The best part is, you can prove your programs before even touching a computer.

I guess some hardcore C programmers who might have a solid understanding of Hoare logic could also do this, but it's far easier in functional languages (my only experience in functional programming is with Haskell, it could very well apply to other functional languages though).

---

### Post by CptPicard on 2009-02-18
> **matthew.ball said:**
> 
I guess some hardcore C programmers who might have a solid understanding of Hoare logic could also do this, but it's far easier in functional languages (my only experience in functional programming is with Haskell, it could very well apply to other functional languages though).

Just get to know some of our hardcore C programmers who have 80 years of experience in the industry, in teams of thousands of programmers... you will be disabused of your silly notions. They don't *need* to prove anything to anyone, as they know *you* are just simply stupid for talking about structural induction and other humbug. They simply see *no need* to know a closure even if it hit them in the face! ;)

Seriously speaking, now I know that that stuff was called "Hoare" logic that I took at uni. It was one of the harder classes I took... although derivations of algorithms from the invariants sometimes produce surprising outcomes.

---

### Post by matthew.ball on 2009-02-18
Last semester I did a course on Formal Proofs, we touched on structural induction/haskell proofs initially, though a lot of it was assumed knowledge from an earlier course (which I did not take).

We eventually got onto Hoare logic, and finally Turing machines (this was the pre-req to "Principles of Programming Languages" :D ).

Very difficult course, but so rewarding.

---

### Post by Gordon Bennett on 2009-02-19
Since there are so many languages to learn functional programming, how about thinking of a project to do, use the various ones suggested and apply this formula:

for (each_language) [
b = time_spent_making_something_useful_with_it
c = time_spent_jerking_off_about_the_language's_syntax
]

And lean towards the ones that have b < c.

---

### Post by nvteighen on 2009-02-19
> **Gordon Bennett said:**
> Since there are so many languages to learn functional programming, how about thinking of a project to do, use the various ones suggested and apply this formula:

for (each_language) [
b = time_spent_making_something_useful_with_it
c = time_spent_jerking_off_about_the_language's_syntax
]

And lean towards the ones that have b < c.
Then, Lisp is the all-winner... just one syntactic form to rule it all. :)

---

### Post by CptPicard on 2009-02-19
> **Gordon Bennett said:**
> 
c = time_spent_jerking_off_about_the_language's_syntax


It's not the syntax, it's the semantics that turn me on! The syntax is often really simple (especially in Lisp), and most of the time it is also just superficial and thus meaningless (excluding in Lisp, where the syntax actually means a lot)...

---

### Post by howlingmadhowie on 2009-02-19
> **nvteighen said:**
> Then, Lisp is the all-winner... just one syntactic form to rule it all. :)

steve yegge had a good blog post about this: [clickity]("http://steve-yegge.blogspot.com/2007/12/codes-worst-enemy.html").

enjoy!

---

