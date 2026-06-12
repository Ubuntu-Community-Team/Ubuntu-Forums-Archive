---
title: "Trying to get better in programming - But how?"
date: 2008-05-17
forum: Programming Talk
---

### Post by Majorix on 2008-05-17
What is a good way for an intermediate programmer (not a beginner to OOP, but somewhat new to functional programming) to learn

**1. Python:**
a. Dive Into Python alone. I have skimmed through it a little. It was ok, but it's rather long. It's like a short tut + a cookbook in one.
b. The official tutorial and a cookbook. I have gone through the official tutorial too but not a cookbook.
c. Something else?

**2. Java:**
a. The official tuts alone. However it would be a little boring and too long to read through. It may be the worse scenario.
b. I would go with the same mentality in 1b (a short tutorial + a cookbook) but I couldn't find a tutorial (the official tutorial is too large in this case) and I haven't looked up any recipe books. If you know of a short and up-to-date tutorial and a good cookbook, I would be very glad to hear it.
b. Some other way?

If you ask me, I would go with b in both (short tut + cookbook) unless someone shows me a better option.

Please comment.

---

### Post by pmasiar on 2008-05-17
Are you afraid of becoming too good? Why not learn both, and more?

---

### Post by Majorix on 2008-05-17
I want to learn Python (for amusement) and Java (for job availabilities) at the moment. How many more can I learn at a short time?

Please post more contributive replies :)

---

### Post by Majorix on 2008-05-17
oops, the browser failed and posted twice.

---

### Post by Lster on 2008-05-17
You could always look at Project Euler ([http://projecteuler.net/](http://projecteuler.net/)) which has nearly 200 problems at many different skill levels.

---

### Post by CptPicard on 2008-05-17
> **Majorix said:**
> What is a good way for an intermediate programmer (not a beginner to OOP, but somewhat new to functional programming)

In particular when it comes to functional programming, the most important issue is learning to "think different". It takes some effort to twist your brain away from the "how" mentality to the "what" kind. It is about seeing the problem in a different light, not about learning anything about the language itself.

I would suggest you check out the Abelson-Sussman lectures that use Scheme to teach the contents of SICP the book. Scheme the language is trivial by syntax, but it is mind-blowing what you can do with it, and what it tells you about programming in general once you "get it".

Me, for one, am spoiled for life... my Java is full of weird contraptions to fake functional-programming concepts.

---

### Post by pmasiar on 2008-05-17
> **Majorix said:**
> How many more can I learn at a short time?

It is not about cramming syntax of more languages. It is about becoming well versed  in libraries, language idioms, best practices, about **solving problems**. Say in Python, learn Django for web apps, maybe Satchmo the e-shop, and you may get better (and more interesting) job than replaceable java monkey. Once you know syntax, problems are language-independent.

---

### Post by Majorix on 2008-05-18
@pmasiar:
It's true that scripting languages are on a rise, but I am not sure about where I live (Turkey). However I guess I will be able to take over the job of a script programmer if I become fluent in a scripting language too. But yeah, mainly it is for my leisure times.
And about the rest, I believe a good cookbook would give you the necessary knowledge to put your skills into use.

@CptPicard:
Did I get it wrong or are you suggesting that I learn Scheme?

@Lster:
I AM looking around for any challenges (like, I have been trying to solve a few levels of the Python Challenge with my limited knowledge of Python).

My questions regarding where I could learn these from remains :lolflag:

---

### Post by CptPicard on 2008-05-18
> **Majorix said:**
> 
Did I get it wrong or are you suggesting that I learn Scheme?


Yeah, why not. There is essentially no syntax -- you can learn the *syntax* of Scheme from this:

Scheme code consists of nested lists (x y z ...) where x, y, z ... are either symbols or similar lists. X is interpreted as function, and y z are its parameters. The value of the list is there result of the function application. The parameters are evaluated before the function call.

The lists themselves are recursive structures of so-called cons pairs which is essentially a simple generalization of a variable to one where there are two slots, car and cdr. The list is terminated by the empty list '() (the symbol 'nil) in the cdr position of the pair.

In addition to this basic structure, there is a small number of so called special forms which outwardly conform to the list evaluation behaviour.

... and it's amazing that Scheme includes essentially all imaginable programming paradigms -- you can roll your own easily. A lot of new thinking to be learned there. It's a great academic language; for a more practical Lisp see Common Lisp which I am hacking in at the moment. I do like some features of Scheme over CL... if there was some kind of überlisp I'd take features from both and combine the best parts.

---

### Post by Bichromat on 2008-05-18
> **CptPicard said:**
> [...] if there was some kind of überlisp I'd take features from both and combine the best parts.

Doesn't Lisp make it easy to create your own language ? :)

---

### Post by CptPicard on 2008-05-18
> **Bichromat said:**
> Doesn't Lisp make it easy to create your own language ? :)

Yeah, most of the time, but there are things in Scheme you just can't emulate in CL... lazy evaluation by yield, ability to have functions and values in the same namespace, continuations to name a few things off the top off my head.

---

