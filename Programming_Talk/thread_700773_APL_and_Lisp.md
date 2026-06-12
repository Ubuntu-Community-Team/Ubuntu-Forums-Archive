---
title: "APL and Lisp"
date: 2008-02-18
forum: Programming Talk
---

### Post by Fbot1 on 2008-02-18
Well, here it is.

---

### Post by Wybiral on 2008-02-18
Huh?

---

### Post by Fbot1 on 2008-02-18
> **Wybiral said:**
> Huh?

> **pmasiar said:**
> Guys can you **please** start your own thread to discuss APL and Lisp? This thread is linked from stricky and as such might be held to higher standards - especially from regulars, who should know better.
.

---

### Post by pmasiar on 2008-02-18
and you may ask LaRoza to move the discussion from Python thread here too.

---

### Post by CptPicard on 2008-02-18
> **Fbot1 said:**
> Because a "functional perspective" isn't important.

Sure it is. You're suggesting APL essentially for the same reason, although it is a far more esoteric language in general than Lisp is -- you even need your own keyboard for it, in the worst case.

The reason why a mathematician is going to like a functional language is exactly the fact that it packages things in functional terms, which is closer to mathematics than using, say, an imperative language.

> Even if it was, they wouldn't use Lisp because it doesn't enforce functional programing and Haskell is closer to Lambda calculus.

Why does it have to enforce it? I don't understand why you "should not have the option of using state" if you want to be a functional programmer.

I use Lisp (Scheme) every now and then, and sure I use a closure when I want one -- and I still use Lisp *exactly because* I get the functional perspective, regardless of having state. I do not strive for functional purity intentionally, but I do get the benefits of the approach.

I'm not really sure how being close to lambda calculus is a good thing for a tool language for a mathematician... if you're into language theory, sure, but not otherwise...

> You're right, it isn't very different but, APL is still used more often then Lisp.

I really would like seeing some kind of evidence for this argument. Maybe actuaries use it (I suppose you got that from the Wikipedia article? :) ), but I sure haven't even seen any APL code that wasn't an example, and I've actually been to a math department...

---

### Post by Fbot1 on 2008-02-18
> **CptPicard said:**
> Sure it is. You're suggesting APL essentially for the same reason, although it is a far more esoteric language in general than Lisp is -- you even need your own keyboard for it, in the worst case.

No, I said APL because I've seen it more

> The reason why a mathematician is going to like a functional language is exactly the fact that it packages things in functional terms, which is closer to mathematics than using, say, an imperative language.
Okay, that's just wrong. Imperative languages are no further from mathematics then functional languages.

> Why does it have to enforce it? I don't understand why you "should not have the option of using state" if you want to be a functional programmer.
Because that's what functional program really is.

> I do not strive for functional purity intentionally, but I do get the benefits of the approach.
Then obviously it's not the functional purity that matters.

> I'm not really sure how being close to lambda calculus is a good thing for a tool language for a mathematician... if you're into language theory, sure, but not otherwise...

because it's widely known.

> I really would like seeing some kind of evidence for this argument. Maybe actuaries use it (I suppose you got that from the Wikipedia article? :) ), but I sure haven't even seen any APL code that wasn't an example, and I've actually been to a math department...


I was going to say statisticians but I said actuaries (I like to see if Wikipedia words it better).

---

### Post by CptPicard on 2008-02-18
> **Fbot1 said:**
> No, I said APL because I've seen it more

Where?

> Okay, that's just wrong. Imperative languages are no further from mathematics then functional languages.

Imperative languages make you specify *how* you achieve a certain result, while functional languages in general allow you to define your function more directly in terms of the mathematical definition. Functional programming is therefore conceptually closer to mathematics.


> 
Because that's what functional program really is.
...
Then obviously it's not the functional purity that matters.


First of all, your latter remark is correct in the sense that functional purity doesn't necessarily matter.

On the other hand you're presenting a false dilemma as you're putting way too much weight on functional purity, claiming that all usage of state is an admission of the failure of the functional paradigm. It quite simply is not so. You may need pure-functional code for some particular needs, and a lot of math problems actually are quite naturally expressed without state as they are.

When you do need state, you can have state. And you still get to keep your problem decomposition in terms of first-class functions calling each other -- while being evaluated in possibly changing contexts, which is essentially the deeper meaning of state in functional programming. The ability to have state when called for is not a weakness.

Out of curiosity, how much Lisp have you written?

> 
because it's widely known.


Lambda calculus is more of a CS concept. I'd be surprised if a mathematician would enjoy expressing his particular problem domain in terms of LC, or if being "close to LC" would be of much benefit.

In comparison to Haskell, Lisp, Scheme in particular, has the added benefit of simplicity -- I'm not dissing Haskell per se, it's probably an interesting tool to use for the same reasons of "functionality" as Lisp is, but Lisp gets you going pretty quickly. YMMV. No reason to assume Lisp is any weaker, though.

---

### Post by Fbot1 on 2008-02-18
> **CptPicard said:**
> Where?

](*,)

> Imperative languages make you specify *how* you achieve a certain result, while functional languages in general allow you to define your function more directly in terms of the mathematical definition. Functional programming is therefore conceptually closer to mathematics.
No, mathematically there is no difference.

> First of all, your latter remark is correct in the sense that functional purity doesn't necessarily matter.
So it's not about how functional it is?

> Out of curiosity, how much Lisp have you written?
Not all that much

> Lambda calculus is more of a CS concept. I'd be surprised if a mathematician would enjoy expressing his particular problem domain in terms of LC, or if being "close to LC" would be of much benefit.
It would because most would know it (and there's no useful ZF language). Also, Lambda calculus has more to do with math then computer science.

---

### Post by CptPicard on 2008-02-18
> **Fbot1 said:**
> ](*,)

My feelings exactly.. ;) You do have a tendency to pull opinions out of your hat and then just to argue for the sake of it with one-liners... APL might be used by actuaries somewhere, but seriously, I haven't seen it in academia in at least those CS/Math circles I've been part of :)

> 
No, mathematically there is no difference.


This is the same argument as the one about Turing-equivalence. I could say that this whole discussion is moot because the mathematicians could just as well be using BrainFuck instead of APL or Lisp, but that's not the point, is it?

> 
So it's not about how functional it is?


As I explained, it is not that black and white at all, and doing down that path is not going to advance this in any way. Are you seriously suggesting that all functional languages which are not strictly "pure" and also enforce that too (by *not* giving you the ability to rewrite your bindings), are of no benefit in the functional sense? Please. Nothing forces or even expects you to use "set!" in Scheme if you don't want to. That's all there really is to keeping yourself pure.

It is quite interesting that you would argue for a low-level imperative language like C -- which has none of the functional tools, first-class functions, lambdas and closures being the most important -- and even resort to the Turing-equivalence defense (an ultimate defense that can always be escaped into), but consider it a horrible shortcoming of Lisp that it *allows* state changes, while having a boatload of other stuff you could never have in C...

> 
Not all that much


Thought so. :p

> It would because most would know it (and there's no useful ZF language).

I wouldn't bet on that. Plus, a mathematician is more likely to want a higher-level abstraction than LC...

> Also, Lambda calculus has more to do with math then computer science.

To be exact, Lambda Calculus is the foundational math of Computer Science, so I'd say it has a lot to do with CS... after all, it was pretty much created as a minimal abstraction that can be used to prove things about "mechanical" computation. It is useful as such, but I'd be very sceptical whether any mathematician would actually want to "code LC" to solve actual mathematical problems ;)

---

### Post by pmasiar on 2008-02-18
> **Fbot1 said:**
> No, I said APL because I've seen it more

It is very hard to argue with a person like you, for whom personal anecdotes hold the same sway as facts, and who does not bother to substantiate any of own claims. You are like a leech who forces other to disprove you by digging out facts - which you can freely dismiss anyway.

But here it goes: [TIOBE](http://www.tiobe.com/tpci.htm) ranks Lisp/Scheme at 20th position, APL unranked between 51 and 100.

Not like I hope you may change in your ways :-)

---

### Post by Fbot1 on 2008-02-19
> **CptPicard said:**
> My feelings exactly.. ;) You do have a tendency to pull opinions out of your hat and then just to argue for the sake of it with one-liners... APL might be used by actuaries somewhere, but seriously, I haven't seen it in academia in at least those CS/Math circles I've been part of :)

I never said it was widely used in academia. Also just because I disagree with you doesn't mean I'm just spiting stuff out; if anything, you are the one who is just flatly disagreeing basically because you think Lisp is just so much better than APL and that it can't possibly be used more often. From my experiences APL is used more than Lisp. It's that simple. If your experiences say otherwise, fine. I am not a liar because I disagree.

> This is the same argument as the one about Turing-equivalence. I could say that this whole discussion is moot because the mathematicians could just as well be using BrainFuck instead of APL or Lisp, but that's not the point, is it?
That's not what I'm saying. I'm saying you can't use that as a reason.

> 
As I explained, it is not that black and white at all, and doing down that path is not going to advance this in any way. Are you seriously suggesting that all functional languages which are not strictly "pure" and also enforce that too (by *not* giving you the ability to rewrite your bindings), are of no benefit in the functional sense? Please. Nothing forces or even expects you to use "set!" in Scheme if you don't want to. That's all there really is to keeping yourself pure.

Then obviously it's functionality isn't important so it must be something else that is related to it.

> To be exact, Lambda Calculus is the foundational math of Computer Science, so I'd say it has a lot to do with CS... after all, it was pretty much created as a minimal abstraction that can be used to prove things about "mechanical" computation. It is useful as such, but I'd be very skeptical whether any mathematician would actually want to "code LC" to solve actual mathematical problems ;)
No, Lambda Calculus started out as yet another attempt to establish a foundation for math.

> **pmasiar said:**
> It is very hard to argue with a person like you, for whom personal anecdotes hold the same sway as facts, and who does not bother to substantiate any of own claims. You are like a leech who forces other to disprove you by digging out facts - which you can freely dismiss anyway.

But here it goes: [TIOBE](http://www.tiobe.com/tpci.htm) ranks Lisp/Scheme at 20th position, APL ranked between 51 and 100.

Not like I hope you may change in your ways :-)

Sure, my experiences/memories/anecdotes/whatever do hold as much as facts because they're the same to _***me***_. That link isn't convincing at all, it doesn't only include projects for math and it doesn't include code that doesn't make it to the internet (which would probably be the majority of it). Also, how do you suppose I prove to you that I've seen APL more then Lisp? Take some test and send it to you?

---

### Post by pmasiar on 2008-02-19
> **Fbot1 said:**
> Sure, my experiences/memories/anecdotes/whatever do hold as much as facts because they're the same to _***me***_. That link isn't convincing at all,

[http://en.wikipedia.org/wiki/Q.E.D](http://en.wikipedia.org/wiki/Q.E.D).

---

### Post by Fbot1 on 2008-02-19
> **pmasiar said:**
> [http://en.wikipedia.org/wiki/Q.E.D](http://en.wikipedia.org/wiki/Q.E.D).

It's the same for you too.

---

