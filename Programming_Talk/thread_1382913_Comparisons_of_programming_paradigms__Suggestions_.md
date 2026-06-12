---
title: "Comparisons of programming paradigms:  Suggestions wanted"
date: 2010-01-16
forum: Programming Talk
---

### Post by BattlePanic on 2010-01-16
It would be interesting to see the same problem solved in different ways, each one employing a different paradigm.  Object-oriented, procedural, declarative, functional

Most of the material I come across tends to focus on a specific style but doesn't provide much in the way of side-by-side comparisons.  Can any of you recommend some texts or online material which compares and contrasts different programming paradigms?

---

### Post by Senesence on 2010-01-16
> **BattlePanic said:**
> It would be interesting to see the same problem solved in different ways, each one employing a different paradigm.  Object-oriented, procedural, declarative, functional

Most of the material I come across tends to focus on a specific style but doesn't provide much in the way of side-by-side comparisons.  Can any of you recommend some texts or online material which compares and contrasts different programming paradigms?

This would interest me as well.

---

### Post by c0mput3r_n3rD on 2010-01-16
There are a few good out there about algorithms.  one of which I have is "Cambridge University Press How To Think About Algorithms".  The ebook is too big so attach to the forum but if you wanted me to e-mail it to you I would be more than happy.  It talks about all the Different programming paradigms through about 27 chapters of selective reading.  You can also just download it as a torrent from [thepiratebay.com]("http://ubuntuforums.org/thepiratebay.com").

---

### Post by nvteighen on 2010-01-17
For imperative vs. functional, you can take a look on [SICP]("http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-1.html"). There's a section in which a declarative-like language is created and contrasted to functional programming too.

---

### Post by CptPicard on 2010-01-17
If there is anything I have learned from my discussions (mostly here) over the past couple of years regarding programming paradigms, it is that it is remarkably difficult to communicate about their differences using just some sort of small program snippets. The ideas are "generally applicable", so any given small piece of code will just be an incredibly narrow example that does not carry across the point of "why this idea is generally important/useful" -- there is always the disingenious counter-argument that "but I will be able to do it in an imperative language *like this*". The paradigm-issues are really very overarching and penetrate the entire nature of the whole program; it's hard to isolate them.

There is no substitute to doing it yourself and letting it affect your thinking... :)

---

### Post by BattlePanic on 2010-01-17
Thanks for the input.  I'd agree that these sorts of concepts are most easily grasped when viewing them on a scale larger than a few simple code snippets.  The subject of programming paradigms could easily fill a few books.

When it comes to designing a program, with a little time and effort, I can usually figure out how *I* would solve a given problem.  However, I usually find that I'm still curious to know how someone else might have designed and coded a different solution to the same problem.

What I would love to find is a book that starts by presenting a non-trivial, complex problem and dedicates the rest of the book to presenting several different programming solutions to that problem from start to finish.

---

### Post by supershin on 2010-01-17
That would be very interesting. 

There should be procedural vs object oriented(OO) comparisons availble. Though it usually is like Turbo pascal vs C or java. I guess the main difference is the objects since C/java can be used to make procedural programs. Though java is built on the OO concept so I won't say it can make a 'pure' procedural program. 

As for declarative and functional, haven't really used these but wiki says functional is a type of declarative, which is apparently an umbrella term.

EDIT: Apparently SQL is declarative, so if the problem is to get info from an array/table, do a sort/filter op and display it. Then sure you could program using these 3 paradigms.

Now came across this link
[http://en.wikipedia.org/wiki/Comparison_of_programming_paradigms]("http://en.wikipedia.org/wiki/Comparison_of_programming_paradigms")

I guess if you want a program that uses all those paradigms the characteristics of the problem must be such that
it can be solve by the paradigm. You aren't going to use sql to create a video game are you.

---

### Post by grayrainbow on 2010-01-17
Nowadays almost nobody use let's say pure procedural or pure functional style for complex programs, they are usually mix of few paradigms. Object oriented programming does not fit in the group, couse it's kinda useless by itself, and by definition objects use some other style for their internal workings. That's in contrast with logic programming, which is by itself extremely declarative, alto so declarative that some people wont call it computer programming at all, but quite interesting subject IMO :) .

Of course all that does not hold for some very special complex beasts like OS kernel and some device drivers.

---

### Post by phrostbyte on 2010-01-17
Here a function which generates the Fibonacci sequence in Haskell (functional language):

> 
fib 0 = 0
fib 1 = 1
fib n = fib (n-1) + fib (n-2)


Notice how this is basically the mathematical definition for the Fibonacci sequence. But it's also a compilable Haskell program. Haskell's declarative approach is very similar to the language of mathematics.

---

### Post by CptPicard on 2010-01-17
Fibonacci sequence is a pretty good demonstrator. The above is the "naive definition" -- the thing can be approached functionally in a lot of different ways (in particular see the "canonical zipWith" example... it demonstrates how functional programming often exposes structure of the problem):

[http://www.haskell.org/haskellwiki/The_Fibonacci_sequence](http://www.haskell.org/haskellwiki/The_Fibonacci_sequence)

Imperatively, you either have the two-state-variable or the naive recursive definition...

---

