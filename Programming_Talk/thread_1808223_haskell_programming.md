---
title: "haskell programming"
date: 2011-07-20
forum: Programming Talk
---

### Post by manish411 on 2011-07-20
I have read the book "learn you haskell for a great good" and I have developed some strong concepts about
functional programming and Haskell but I dont know where to proceed. Can someone please guide me 
to further study in this language which can help me in Haskell internships or jobs!!

---

### Post by TwoEars on 2011-07-20
> **manish411 said:**
> I have read the book "learn you haskell for a great good" and I have developed some strong concepts about
functional programming and Haskell but I dont know where to proceed.
Well, have you actually tried writing any of your own code? Having the concept is great, but you also need to know how to convert concepts to code. Try some challenges and see how you get along.

> 
 Can someone please guide me 
to further study in this language which can help me in Haskell internships or jobs!!
Well, I don't know about in your area, but around where I live, there's very very few Haskell-based jobs and even fewer internships. I suggest joining haskell mailing lists - people often advertise jobs on there. You can also see this - [http://hackage.haskell.org/trac/ghc/wiki/Internships](http://hackage.haskell.org/trac/ghc/wiki/Internships), [http://cufp.org/jobs](http://cufp.org/jobs) (note how there's a grand total of 1 job based on Haskell there), Haskellers.com (note how there's no jobs on here) and again, 0 jobs on [http://functionaljobs.com/](http://functionaljobs.com/) .

---

### Post by ceclauson on 2011-07-22
We're in almost the same boat, but I might be a little further along.  I'd recommend the book "Real World Haskell" by the O'Reilly publishers.  It has a website:

[http://book.realworldhaskell.org/]("http://book.realworldhaskell.org/")

The chapter on I/O (Chapter 7) is pretty good.  After reading this chapter, I was able to write text processing programs in Haskell.

---

### Post by LemursDontExist on 2011-07-22
If you're just looking for a good way to practice Haskell, I'd suggest trying [Project Euler]("http://projecteuler.net/index.php?section=problems").  Figuring out how to work through 50 or so of those problems in Haskell will give you a very solid practical grasp of functional programming, while also being an excellent refresher on algorithms generally.

---

### Post by schauerlich on 2011-07-22
> **LemursDontExist said:**
> If you're just looking for a good way to practice Haskell, I'd suggest trying [Project Euler]("http://projecteuler.net/index.php?section=problems").  Figuring out how to work through 50 or so of those problems in Haskell will give you a very solid practical grasp of functional programming, while also being an excellent refresher on algorithms generally.

I wouldn't say doing Project Euler problems are a great way of gaining practical knowledge. They're mostly math-oriented, which is only useful if you're planning on doing number-crunching or graphics.

---

### Post by LemursDontExist on 2011-07-22
> **schauerlich said:**
> I wouldn't say doing Project Euler problems are a great way of gaining practical knowledge. They're mostly math-oriented, which is only useful if you're planning on doing number-crunching or graphics.

It can take a while to get your head around Haskell syntax - to figure out how to make Haskell do exactly what you want.  Practice taking a bunch of algorithms and coding them to operate correctly in Haskell is a great way to gain some real control over the language.  I'll grant, some other task could just as well be used as a training tool, but Haskell is so well suited to that sort of numerical task that working through the Project Euler problems is very satisfying.

In any case, a solid grounding in problem solving and algorithms is the basis of solid programming.  The problems they'll ask you if you apply for a job at Google or Microsoft aren't so very different from the Project Euler problems, and there's a reason for that.  If manish411 isn't looking for a job at a place like Google, Haskell is a very odd choice of language.

---

### Post by TwoEars on 2011-07-22
> **LemursDontExist said:**
> It can take a while to get your head around Haskell syntax - to figure out how to make Haskell do exactly what you want.  Practice taking a bunch of algorithms and coding them to operate correctly in Haskell is a great way to gain some real control over the language.  I'll grant, some other task could just as well be used as a training tool, but Haskell is so well suited to that sort of numerical task that working through the Project Euler problems is very satisfying.

In any case, a solid grounding in problem solving and algorithms is the basis of solid programming.  The problems they'll ask you if you apply for a job at Google or Microsoft aren't so very different from the Project Euler problems, and there's a reason for that.  If manish411 isn't looking for a job at a place like Google, Haskell is a very odd choice of language.

Google doesn't look for Haskell programmers, you can use it internally if you want, but they don't look for it. They don't look for a language at all, actually, most of the time it's based on your general intelligence.

---

### Post by schauerlich on 2011-07-23
> **LemursDontExist said:**
> It can take a while to get your head around Haskell syntax - to figure out how to make Haskell do exactly what you want.  Practice taking a bunch of algorithms and coding them to operate correctly in Haskell is a great way to gain some real control over the language. 

I guess. The syntax is a little odd, but conceptually the type system is much more challenging. You aren't going to be doing anything terribly interesting in Haskell when all of your functions are Int -> Int.

> **TwoEars said:**
> Google doesn't look for Haskell programmers, you can use it internally if you want, but they don't look for it. They don't look for a language at all, actually, most of the time it's based on your general intelligence.

A google recruiter who came to my university's campus last year said that they look specifically for programmers who are skilled with Python, C++ and/or Java, as those are the languages they prefer internally.

---

### Post by TwoEars on 2011-07-23
> **schauerlich said:**
> A google recruiter who came to my university's campus last year said that they look specifically for programmers who are skilled with Python, C++ and/or Java, as those are the languages they prefer internally.

You need to know one of the "big" three there, Java, C/C++, or Python, but as long as you can think on your feet they don't mind too much. ;) You obviously need to know the core of CS though.

---

