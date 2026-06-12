---
title: "25 years of C++"
date: 2010-10-15
forum: Programming Talk
---

### Post by spjackson on 2010-10-15
It's 25 years since the first publication of Stroustrup's The C++ Programming Language
[http://www.wired.com/thisdayintech/2010/10/1014cplusplus-released/all/1](http://www.wired.com/thisdayintech/2010/10/1014cplusplus-released/all/1)

---

### Post by James78 on 2010-10-15
I can't believe I just read all of that. :/

---

### Post by StephenF on 2010-10-15
Not nearly as bad as reading C++ code but about as informative.

---

### Post by maximinus_uk on 2010-10-15
If we're lucky it might die a death before it hits forty!

---

### Post by krazyd on 2010-10-15
> **StephenF said:**
> Not nearly as bad as reading C++ code but about as informative.

> **maximinus_uk said:**
> If we're lucky it might die a death before it hits forty!

I've never understood all the hate C++ gets. I find it very powerful and expressive.

I liked this quote:
> I’ll just note that I consider the idea of one language, one programming tool, as the one and only best tool for everyone and for every problem infantile. If someone claims to have the perfect language he is either a fool or a salesman or both.

---

### Post by Reiger on 2010-10-15
C++ is useful, but:

(a) For true systems programming, C might be altogether better choice as it is a more concise language. In practice this means that the language (as implemented, not as specified) is fairly predictable for even intermediate programmers (it does what it says: less undefined or buggy behaviour).
(b) For a high level language C++ is simply too tied up in being a systems programming language to work cleanly. Famously exceptions in C++ can not work without a lot of meticulous programming effort on the part of implementer and recipient lest memory leaks occur. 

Buffer overruns, underruns, null pointers and lack of boundary checking do not help either.

But where this truly shows is the notion that you can cast everything to a void pointer, overwrite memory to access formerly private data members; and back to a desired type. It simply speaks volumes as to why C++ is more C with extensions than a true high level language.
---------------------------------------------------

In practice, C++ might be all you've got; and in practice there are a lot of abstractions built on top of C++ to use it in less cumbersome fashions, but it should be recognised that neither are any form or merit on the part of the language itself.

---

### Post by Zanthir on 2010-10-15
I think C++ is great. You get nitty gritty control of the computer if you want it, and high level programming (without a VM) if you want it too. What could be better?
> (a) For true systems programming...
(b) For a high level language...Although you pointed these things out as flaws, note that you are mentioning that it does both. That's magic.

---

### Post by nvteighen on 2010-10-15
Happy Birthday!

> **krazyd said:**
> I've never understood all the hate C++ gets. I find it very powerful and expressive.


I don't like C++, but I'll try to keep this as neutral as possible. The main argument against C++ is the following: 

"It's a mess" (i.e. Mixed not-separable abstraction layers). C++ aims to target everything. So, in one hand you've got the low-levelness of C and in the other, the high-levelness of the STL, both placed into the same language, but you can't separate them at all. If you only use the low-level features, you get C... no matter whether you use a C++ compiler for it: it's still C. If you aim to use only OOP and STL C++, you just can't get rid of the low-level details because as soon as you need to overload operator=, you need to know how references work... and they don't work exactly as Java references. So, some (like me) consider this to be a messy language design; others think this is a feature that allows for flexibility. What can't be denied is that this makes C++ a language very difficult to master.

I won't dive into the details of why I believe that argument to be correct... because, like it or not, C++ is a huge milestone in programming history and this thread should celebrate its 25th anniversary :); my intention here was only to describe the argument.

---

### Post by MadCow108 on 2010-10-15
> **nvteighen said:**
> Happy Birthday!



I don't like C++, but I'll try to keep this as neutral as possible. The main argument against C++ is the following: 

"It's a mess" (i.e. Mixed not-separable abstraction layers). C++ aims to target everything. So, in one hand you've got the low-levelness of C and in the other, the high-levelness of the STL, both placed into the same language, but you can't separate them at all. If you only use the low-level features, you get C... no matter whether you use a C++ compiler for it: it's still C. If you aim to use only OOP and STL C++, you just can't get rid of the low-level details because as soon as you need to overload operator=, you need to know how references work... and they don't work exactly as Java references. So, some (like me) consider this to be a messy language design; others think this is a feature that allows for flexibility. What can't be denied is that this makes C++ a language very difficult to master.

I won't dive into the details of why I believe that argument to be correct... because, like it or not, C++ is a huge milestone in programming history and this thread should celebrate its 25th anniversary :); my intention here was only to describe the argument.

#2
I too like the language and use it a lot.
But the design is just terrible and it is impossible to teach (in a timely manner).
It has sooo many pitfalls (vexing parse, inherited copy constructors ...)

If you want to see how bad c++ is, go into (non-computer) science.
Almost no one spends the 2-3 years it takes to learn c++ but still everybody uses it and the result is a huge amount of terrible software :/

But if you master the language you can write some impressive stuff.

---

### Post by krazyd on 2010-10-17
> **Reiger said:**
> In practice, C++ might be all you've got; and in practice there are a lot of abstractions built on top of C++ to use it in less cumbersome fashions, but it should be recognised that neither are any form or merit on the part of the language itself.
I see your point and certainly agree. I generally use Qt which tends to take a lot of the pain out of standard C++. But of course it is just an abstraction.

---

### Post by worksofcraft on 2010-10-17
> **krazyd said:**
> I see your point and certainly agree. I generally use Qt which tends to take a lot of the pain out of standard C++. But of course it is just an abstraction.

I think the fact that it lets you construct said abstraction says a lot about the versatility of the language.

Certainly much dodgy code has been written but IMO there is little excuse for doing so in C++ and it is more an indictment of the programmer's abilities than of the language.

In analogy just because one is able to utter foul profanity in English it doesn't make English the language of the gutter :shock:

---

### Post by CptPicard on 2010-10-17
I've never quite understood the claim that C++ manages to build abstraction on top of machine-specific primitives... it's not particularly abstract (classes are just a type-system extension mechanism for example), and IMO it is debatable whether it bridges the gap to higher-level constructs that well... there certainly is a lot of gotchas one needs to be aware of while using abstractions, as the supposedly hidden machine-specifics always leak into the consideration...

Also, programming languages are tools... they exist because we don't like banging ones and zeroes into the machine. So the argument that it's all about programmer competence, no matter how badly a tool might be designed, sounds like an excuse :)

That said, it is certainly true that C++ is currently a "best effort" kind of solution for the particular problem of maintaining proximity to the machine while introducing "abstraction" into the language... I do personally prefer Objective-C style designs for this particular niche, though.

---

