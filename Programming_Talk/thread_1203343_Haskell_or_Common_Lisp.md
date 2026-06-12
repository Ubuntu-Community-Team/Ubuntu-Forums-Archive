---
title: "Haskell or Common Lisp"
date: 2009-07-03
forum: Programming Talk
---

### Post by cdiem on 2009-07-03
I'd like to pick a functional programming language, as I've read many posts regarding how well this could influence further programming in languages such as Java, C, Python, etc. (my interests are in Java programming). I'm currently having a doubt choosing between Haskell and Common Lisp.  
Which one would you recommend me?

---

### Post by CptPicard on 2009-07-03
Well, either... but I would suggest Lisp. Simply because it is a multi-paradigm language, it does not force pure-functionality on you from the start. The basics of lisp are also really simple to grasp... and you can write FP-style code in Lisp as much as you want, and use side-effects when you feel like you need them.

Of course Lisp can't give you the theoretical guarantees of no side effects like Haskell can, but you are not interested in that stuff yet... and when you are, you can move to Haskell.

---

### Post by nvteighen on 2009-07-03
> **cdiem said:**
> I'd like to pick a functional programming language, as I've read many posts regarding how well this could influence further programming in languages such as Java, C, Python, etc. (my interests are in Java programming). I'm currently having a doubt choosing between Haskell and Common Lisp.  
Which one would you recommend me?
Common Lisp is not pure-functional... It's actually a multi-paradigm language, while Haskell is only functional. Of course, Common Lisp can be used as a pure-functional language by avoiding some parts of it, but if this worries you somehow, maybe Clojure is the Lisp you want (pure-functional, simple. Runs on the Java Virtual Machine, so you can interface with Java code).

Scheme is another Lisp dialect, also multi-paradigm, but that is also very much used as pure-functional. It also supports Continuation Passing Style (CPS), which may be interesting to you too.

Lisp has an advantage over Haskell: Lisp code <=> Lisp data. Check out the macro system and you'll be able to do really sweet things.

---

### Post by cdiem on 2009-07-03
Thanks for your replies; I think I'll try with Common Lisp and (maybe) later complement it with Haskell. Thanks again.

---

### Post by CptPicard on 2009-07-03
I would suggest that if it is the ideas you're after, Scheme is more approachable than CL while still being Lisp...

---

### Post by cdiem on 2009-07-03
Edit: Now I have taken a closer look at Clojure; I think I really liked what I saw. If this language is going to teach me ideas similar to the ones form CL/Haskell/Scheme, I think I would prefer it over them (it seems more practical to me for my purposes because of its interaction with JVM). Thanks a lot.

---

### Post by hessiess on 2009-07-03
> **nvteighen said:**
> maybe Clojure is the Lisp you want (pure-functional, simple. Runs on the Java Virtual Machine, so you can interface with Java code).

Clojure is a nice functional language, but it isn't pure, the languages website states this

> 
Clojure is impure, in that it doesn't force your program to be referentially transparent


[http://clojure.org/functional_programming](http://clojure.org/functional_programming).

---

### Post by soltanis on 2009-07-03
Purity is not a particularly important property of functional languages (it doesn't impart godlike powers to them), and for the record I would suggest any Lisp over Haskell because one thing that Lisp is that Haskell isn't is consistent in its syntax.

---

### Post by CptPicard on 2009-07-03
> **soltanis said:**
> Purity is not a particularly important property of functional languages (it doesn't impart godlike powers to them)

Well actually purity is a very nifty thing to have from the compiler's perspective -- it allows a lot of reasoning about the program and nice optimizations such as memoization to be applied across the board... not to mention that data-parallelism is much easier when there are no side-effects, ever, anywhere.

On the other hand the cost of this is that writing pure-functional programs can be a bit of a dark art... :)

---

