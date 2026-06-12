---
title: "functional programming"
date: 2010-06-27
forum: Programming Talk
---

### Post by shadylookin on 2010-06-27
I've recently been doing some javascript programming and I've had to use some of the functional language concepts like closures. As a guy who usually uses Object oriented/procedural languages it was an interesting experience. I've heard that learning functional languages improves your thinking as a programmer so I've got some questions. 

For people that have learned functional languages do you really think this is true? Do you think this improved knowledge offsets the fact that I'll probably never be able to put it to use in a real production environment? which functional language would you recommend for someone wanting to learn one?

---

### Post by soltanis on 2010-06-27
1. Oh hell yes.
2. Do you use Javascript? Do you use Python? These are functional languages (they have functional constructs). Even if you use an imperative language or Object-Oriented nonsense (such as C or Java) you can still take important lessons from functional principles (such as function mapping, list reduction, recursion, etc). C does have function pointers and they are useful for things other than just callbacks.
3. ANSI Common LISP (I recommend SBCL, it's the easiest to get going with).

---

### Post by simeon87 on 2010-06-28
1. Absolutely.
2. You will be able to use it with every line of code you write. Functional programming cuts down to the essence of what a function computes which will improve the modularity and clarity of your code, even when it's procedural or OOP.
3. Haskell.

---

### Post by nvteighen on 2010-06-28
1 & 2) Hm... of course. It makes you program from another point of view which may be of use in **any** language. Functional programming techniques can be applied everywhere, even though most languages don't provide native syntax support for it.

3) To start with FP, I'd use Scheme without imperative constructs (it's easy, by convention imperative procedures are named with "!" as suffix). It's smaller than Common Lisp, but it's still Lisp (although Lisp's strength is not to be functional, but its metacircular properties). The MIT SICP videos are really great and use that particular Lisp dialect. Afterwards, Common Lisp (but again, it's multiparadigm).

---

### Post by Reiger on 2010-06-28
Consider unit tests, or the preferred way to handle concurrency in a language like Java (using thread pool implementations provided by the Java standard lib): that is a lot easier to do when your code approaches an FP style then when it is a riddle of global/object state flags.

---

### Post by Reiger on 2010-06-28
EDIT: double post?

---

### Post by Reiger on 2010-06-28
EDIT: triple post, what is the browser/internet connection doing?

---

### Post by dv3500ea on 2010-06-28
> **shadylookin said:**
> I've recently been doing some javascript programming and I've had to use some of the functional language concepts like closures.

Javascript is object oriented and procedural as well as functional. In fact there are a lot of multiparadigm languages. In my opinion the best languages treat functions as objects (like javascript does). 

It is good to learn functional techniques. This may be easier to do in pure functional languages such as [s]lisp[/s] haskell. You can then apply the approaches you've learnt to multiparadigm languages. For example, it is often much more elegant to use functional recursion instead of looping structures like 'while'.

Another thing you may want to look at is prototypal inheritance vs class based inheritance. In my opinion prototypal inheritance is better because it is much simpler. Javascript has a fairly ugly pseudo-classical implementation of prototypal inheritance.

---

### Post by schauerlich on 2010-06-28
> **dv3500ea said:**
> This may be easier to do in pure functional languages such as lisp.

Lisp isn't pure functional, it's multiparadigm. Haskell is a good purely functional language.

---

### Post by Letrazzrot on 2010-06-28
Program long enough, and you *will* eventually use things such as recursion, immutable objects, lambda functions - or else you will be doing things the hard way.  So yes, learning a pure functional language would help with learning these things, but as others have said many languages have (varying) support for these.

Recursion, for example, can make cracking certain algorithms so easy/quick it almost feels like cheating (expression parsing, flood fill, field-of-view are some of the recursive algorithms I've used just recently).  But I have had recursion fail me in C++ (for example), due to stack size limitations.  The good thing about recursion is that you can come up with the recursive algorithm, then convert it into an iterative one without too much work.

The same can be said for lambda functions, and immutable data types are important to writing safe code in today's multi-threaded environs.

A good programmer should have a number of tools available, and IMO these paradigms are important tools to have.  Especially since functional patterns do not seem to come as naturally to most people as OO or procedural patterns.

---

### Post by CptPicard on 2010-07-12
> **shadylookin said:**
> I've recently been doing some javascript programming and I've had to use some of the functional language concepts like closures.

Congrats, that is actually *the* programming language feature, alongside with function definition, function calls (and by extension, hopefully tail-call-eliminated recursion). See lambda calculus -- especially the ability to carry context around. Object-orientedness drops out as a kind of side-effect in "real" functional languages (see how to do simple objects in Scheme).

> 
For people that have learned functional languages do you really think this is true?

Considering that most people who have got into functional programming have behaved almost as if they got religion, myself included, it most certainly is. I never really "got" programming from the Java OOP modelling side before I messed around with a lot of dynamic-typed and functional languages and over time started just treating Java's OOP as "type system extension" with lots of anonymous inner classes...

> 
 Do you think this improved knowledge offsets the fact that I'll probably *never be able to put it to use* in a real production environment?

Oh, this is not true. Computation is moving onto big clusters and highly parallel processors; functional programming is, due to either minimization or elimination of mutable state, very suitable for this stuff. Even if you didn't use a functional programming language, you still will have learned to express solutions in a functional way.

> 
 which functional language would you recommend for someone wanting to learn one?

Scheme, or Common Lisp. This is not to diss Haskell or anything, but it's a bit esoteric and has more obscure stuff for you to learn than you care to begin with, and Lisp on the other hand is a multiparadigm language with functional constructs that you can use to play with functional ideas; and in addition, the core ideas of Lisp that don't deal with FP are actually really informative as well. Understand Scheme and you'll understand how to write interpreters for your own languages in general, for example.

> **simeon87 said:**
> 1. Absolutely.
2. You will be able to use it with every line of code you write. Functional programming **cuts down to the essence of what a function computes** which will improve the modularity and clarity of your code, even when it's procedural or OOP.

This. In FP you typically will need to really know what you're doing, as you're specifying "what" instead of "how". This is probably why competent Haskellers claim that they may spend time thinking about how to express what they want, but once it's there and all typed in, it generally works at first go.


> **nvteighen said:**
> Functional programming techniques can be applied everywhere, even though most languages don't provide native syntax support for it.

Well, the thinking is useful everywhere, but got to admit that languages without higher-order functions or closures or tailcall optimization are a bit lame for FP no matter how hard you tried :)

---

### Post by nvteighen on 2010-07-13
> **CptPicard said:**
> 
Well, the thinking is useful everywhere, but got to admit that languages without higher-order functions or closures or tailcall optimization are a bit lame for FP no matter how hard you tried :)

Of course... but just throw in some function pointers and watch the miracle! :P

Ok, more seriously. The FP techniques can be helpful even in C... For example, you could use stateless programming in C to avoid using a fullfledged struct-as-class approach. Of course, it won't be memory efficient and you better use the stack for them. Something like that may be of use in a program. Closures would be the hardest to do, possibly.

---

### Post by CptPicard on 2010-07-13
> **nvteighen said:**
> Of course... but just throw in some function pointers and watch the miracle! :P

No closures ;) But you know that.

>  For example, you could use stateless programming in C to avoid using a fullfledged struct-as-class approach. Of course, it won't be memory efficient and you better use the stack for them. Something like that may be of use in a program. Closures would be the hardest to do, possibly.

In stateless programming you often are creating a lot of state-objects that as you say better reside on the stack, otherwise we run into memory management issues. Same goes for closures even more; their whole point relies heavily to the fact that their lifecycle is conveniently is managed behind the scenes... that tends to mean a garbage collector. Then there's also the simple issue of closures having to be able to resolve a lexical scope that simply is not available according to the C language's definition -- you'd have to rewrite the compiler :)

---

### Post by xefix on 2010-07-13
I've used Ocaml (ML variant) in the past and can recommend that as a fairly good functional language. There's a huge trading firm (Jane Street Capital) that uses Ocaml to process their transactions, so it's not exactly a useless or "learning" language, either.

---

### Post by shadylookin on 2010-07-14
Well since my post I started learning haskell. I must say it's quite enjoyable.  It's less code and it feels like it flows from my brain easier than any other language I've used. Rather difficult to explain, but it seems like a much more natural way to express yourself. I'm definitely glad I decided to pick it up.

---

### Post by CptPicard on 2010-07-14
Yes, you're working with the problem more than with the language, that's why it flows out of your brain better. I would recommend looking into Lisp too though; the point is that Lisp integrates all approaches through a remarkably small, minimal core language definition. The issue with Haskell, as I see it, is that pure-functionality gets quite challenging for nontrivial tasks, and that Haskell itself as a language is much more complex than the basic Lisp (on top of which Common Lisp has built a big system, though).

---

