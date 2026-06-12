---
title: "Lisp or Haskell?"
date: 2010-03-02
forum: Programming Talk
---

### Post by nmccrina on 2010-03-02
If I was going to learn a functional language without any previous functional experience, which should I go for? Haskell seems to be more purely functional, and I was confused by all the dialects of Lisp out there. Yet Lisp seems to be used a lot more.

Since I don't have time these days to learn both, which would be more valuable to know?

---

### Post by CptPicard on 2010-03-02
Yes, Haskell is pure-functional, which makes you really be pure-functional *all the time*... all the monads and such can get a bit involved. This is of course not a bad thing by any means as far as learning goes -- and pure-functionality has nice theoretical benefits, too -- but with Haskell you should understand that you'll be going all the way, all the time. As a language it is more specialized in nature in that sense.

Lisp on the other hand is "functional" only in part... it is actually totally misunderstood on this count by most. It should be seen as probably the most general *multiparadigm* language in existence, as what it does is that it first abstracts the idea of a programming language itself into a bare minimum set of components, and then allows you to put those back together in pretty much any way you want, producing in the end, if you're so inclined, a specialized computable language for handling your particular task.

You can of course do functional-style programming in Lisp as well. Things like higher-order functions and closures are very integral to Lisp's general machinery. 

So, I would say that Lisp teaches you to program in "any style" (and shows you how they relate to each other), gives you insight into writing interpreters, languages and compilers, and has a surprisingly gentle learning curve to begin with as the basics are simple... Haskell is strictly for the functional-programmer.

---

### Post by nvteighen on 2010-03-02
+1 CptPicard

Actually, Lisp's original feature is its homiconicity, not the functional programming part. In other words, the idea of code being data and data being code is its real distinguishing characteristic on which the whole rest of Lisp is based on.

Well... actually, Forth also took this idea... but I sometimes believe Forth is just a reversed Lisp without parentheses (as it uses Reverse Polish Notation :P).

---

### Post by grayrainbow on 2010-03-02
Actually both are not very used in "real world". Anyway I would go with Scheme. It's simple not bloated like Common Lisp, have very good editor(IDE) in one of it's variants(PLT).

Just to get idea of some of the differences:
Lisp like languages are quite primitive, and you'll have to do a lot of the "most stupid work" that programmer should ever do - namely you'll be the parser(that's the reason for all that parentesis), but that's has really good side - you'll learn a bit what expression tree is. In it's base it support only one style of programming - namely function calls which make it absolutly unsuitable for many problems if one not obuse with some of its futures. And ofcourse in Lisp there is something that I'm not aware of Haskell equivalent - macros, which combined with what nvteighen sad is quite interesting as a concept. Basicly macros are the main reasons so many dialects of Lisp exist, it's extreamly suitable for simple language creation and in place testing.
Haskell on other hand is very suitable for high math concepts, and code in Haskell really look quite natural for some math solutions. But as a general one should consider it before Lisp only if math take priority over algorithmic programming in his/her mind.
As for end - google search model is well known to follow some of the functional programming principles, but the actual API is written in C++. So the question is just how one want to learn some technique - by programming(Lisp, Scheme, Haskell), or just read the concepts of functional programming. Effect is the same in both ways of learning, just most of the times, programmers prefer something involving programming language :)

P.S. Happy coding :)

---

### Post by diesch on 2010-03-02
If you want to learn functional programming I'd go with Haskell as it really is a pure functional language. 

You can use LISP to do functional programming, but LISP doesn't teach you to do so.

---

### Post by CptPicard on 2010-03-02
> **diesch said:**
> You can use LISP to do functional programming, but LISP doesn't teach you to do so.

More like, it doesn't force you to do so -- as it doesn't really force you to do much anything, it's up to you. Then again, understanding the core functional elements is of course remarkably useful (and, well, mandatory), and they do become second nature after some use... so the learning curve into the functional mindset perhaps has a gentler learning curve on the Lisp side. Plus, you certainly have your side-effects when you need/want them.

IMO one of the more interesting features of Haskell that Lisp doesn't have are the algebraic datatypes and the related pattern matching, plus the type-inference engine... which is of course helped a lot by the fact that everything is a pure-functional expression.

---

