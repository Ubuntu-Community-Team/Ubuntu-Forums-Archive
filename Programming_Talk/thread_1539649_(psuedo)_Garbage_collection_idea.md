---
title: "(psuedo) Garbage collection idea"
date: 2010-07-26
forum: Programming Talk
---

### Post by techgeek314 on 2010-07-26
This is a concept I have for how a language could have (hopefully) fast garbage collection.  Before I say this, I want to say that I do know that reference counting is not a new idea.  One of the issues with reference counting is that it does not by itself handle circular references.  What if you just decided that that was the programmer's problem?  This may not be a new idea either...

How fast is reference counting compared to other types of garbage collection?

---

### Post by worseisworser on 2010-07-27
> **techgeek314 said:**
> This is a concept I have for how a language could have (hopefully) fast garbage collection.  Before I say this, I want to say that I do know that reference counting is not a new idea.  One of the issues with reference counting is that it does not by itself handle circular references.  What if you just decided that that was the programmer's problem?  This may not be a new idea either...


The RC GC could detect cycles automatically actually. CPython does this.


> **techgeek314 said:**
> How fast is reference counting compared to other types of garbage collection?

It's usually slower overall (lower throughput) actually, but more predictable in that the pauses are more even even though they happen more often.

Incremental/concurrent garbage collectors reclaim much of the predictability found in the non-GC and RC GC scenarios.

I sometimes think about RC GC in a multi-core scenario; the overall reduction in throughput as seen in a single-core scenario might not be as important there. One will have to use CAS of course. There are some interesting papers out there about recent possible improvements; [http://en.wikipedia.org/wiki/Reference_counting#Dealing_with_inefficiency_of_updates](http://en.wikipedia.org/wiki/Reference_counting#Dealing_with_inefficiency_of_updates)

---

### Post by nvteighen on 2010-07-27
> **techgeek314 said:**
> This is a concept I have for how a language could have (hopefully) fast garbage collection.  Before I say this, I want to say that I do know that reference counting is not a new idea.  One of the issues with reference counting is that it does not by itself handle circular references.  What if you just decided that that was the programmer's problem?  This may not be a new idea either...

How fast is reference counting compared to other types of garbage collection?

Uh, where is it?

Just something: C's attitude is a bit like "This is the programmer's issue". It all depends on what abstraction layer you want to work on: GC is a high-level feature... it makes you forget you're working on a computer with some RAM and makes you live in a "world" where you've got objects that are accessible according to some scoping rules.

---

### Post by techgeek314 on 2010-07-27
What I mean is that you do reference counting and free memory when an "object" 's reference count reaches zero.  If that never happens because of circular references, that is the programmer's problem.

---

### Post by shadylookin on 2010-07-27
That kind of defeats the purpose of garbage collection. If it doesn't abstract all of that worry away then it may as well abstract none of it so you can at least get the benefits of managing memory manually.

---

### Post by techgeek314 on 2010-07-27
How common are circular references?  If they don't occur much, might it be a worthwhile compromise between full garbage collection and manual memory management?

---

### Post by splicerr on 2010-07-28
> **techgeek314 said:**
> This is a concept I have for how a language could have (hopefully) fast garbage collection.  Before I say this, I want to say that I do know that reference counting is not a new idea.  One of the issues with reference counting is that it does not by itself handle circular references.  What if you just decided that that was the programmer's problem?  This may not be a new idea either...


You're right none of them are new ideas ;). You described pretty much how Vala manages memory. Reference counting and weak references to break reference cycles. Only there's no garbage collector.

---

### Post by Nick_Jinn on 2010-07-28
Puppy linux has an option after downloads called "trim fat"....I dont know if that is what you are talking about since I am a novice, but you might look into whatever they are using for that. Try it if you havnt.

---

