---
title: "scheme and lisp"
date: 2010-05-02
forum: Programming Talk
---

### Post by mo.reina on 2010-05-02
quick question for those who are familiar with both scheme and common lisp.  how similar/different is the syntax?  will learning scheme make it easier/harder to switch to common lisp?

---

### Post by dv3500ea on 2010-05-02
They are both dialects of lisp so both have the same syntax. They have slightly different features and libraries but moving from one to the other should be easy enough.

---

### Post by Jesdisciple on 2010-05-02
I haven't yet learned Scheme, but I am fairly far into Common Lisp (not done learning it yet) and the folks who helped me instructed me in many of the differences.  It seemed like every time I found something unintuitive in Common Lisp they said Scheme did it as I expected, so I kinda wish I had started with Scheme now.  I'd be glad to discuss this further in this thread or over PM, as Lisp quickly became one of my favorite topics.

Here's the journal of my experiences thus far, which I temporarily abandoned because of schoolwork: [https://wave.google.com/wave/#restored:wave:googlewave.com!w%252BuE3x3-Z6G](https://wave.google.com/wave/#restored:wave:googlewave.com!w%252BuE3x3-Z6G)

---

### Post by CptPicard on 2010-05-02
Scheme is a kind of straightened-out Lisp because it's more of an academic project... it's minimalized to the point where you can most easily see what the essentials are. Common Lisp is the more practical, hence bigger and somewhat more complex, Lisp.

The basic philosophy is all the same so in that sense there is no difference. One of the biggest tripping points for most seems to be that CL keeps functions and values in different namespaces; this helps with compilation. Scheme does away with the difference, so a function can be treated as a normal value just like everything else.

---

### Post by mo.reina on 2010-05-02
hey chris, i don't have a wave account, so i can't access the link you put up.

so i gather learning scheme, then shifting to common lisp won't be a problem?  i'm just asking because this book was recommended to me [http://www.htdp.org/]("http://www.htdp.org/") for learning lisp and it uses scheme, though i've been told that common lisp is what is mainly used to develop programs.

---

### Post by nvteighen on 2010-05-02
The difference lies in fundamental design decisions, because though syntax is different in some respects (of course both use S-expressions) you could always use a set of macros to make one's syntax like the other's.

Scheme is what's called a Lisp-1, this is a minimalist Lisp dialect which follows the McCarthy's ideas for Lisp more closely and therefore, leading to an academic programming language that's very fragmented into lots of different implementations that only share the little minimum standard and had to add their own non-standard extensions to make themselves practical. 

Common Lisp is what's called a Lisp-2, a more "bloated" language that includes practical resources in the standard itself; this leads to more uniformity and less fragmentation.

---

### Post by Jesdisciple on 2010-05-02
The most commonly recommended Scheme textbook, and the one I will use, is probably *The little Schemer*, which you can read all but one page of [here]("http://books.google.com/books?id=xyO-KLexVnMC&printsec=frontcover&cd=1&source=gbs_ViewAPI#v=onepage&q&f=false").  For Common Lisp I'm using the de facto standard [Practical Common Lisp]("http://www.gigamonkeys.com/book/").

htdp looks like it may be more geared toward the beginning programmer.  I'll try to compare it with *The little Schemer* once I know enough Scheme to have a proper perspective.

I'll start transferring that Wave journal to a blog post...

---

### Post by CptPicard on 2010-05-02
Well, Structure and Interpretation of Computer Programs (SICP) should be mentioned as well...

---

### Post by Cracauer on 2010-05-02
> **mo.reina said:**
> quick question for those who are familiar with both scheme and common lisp.  how similar/different is the syntax?  will learning scheme make it easier/harder to switch to common lisp?

In Lisp syntax doesn't matter in the first place. Except when dealing with compile-time computing (macros etc.) that Scheme doesn't really do.

I don't use Scheme but I'm a heavy Common Lisp user. Learning Scheme is a good experience and will help in getting up to speed in CL but then so is learning something more useful, like CL :)

---

### Post by CptPicard on 2010-05-02
> **Cracauer said:**
> Learning Scheme is a good experience and will help in getting up to speed in CL but then so is learning something more useful, like CL :)

Well... I find that learning Lisping in Scheme very nicely and cleanly teaches you a lot of the really important ideas such as code-data duality and what the minimal set of core abstractions are that you're likely to want in a programming language that will then be able to be used as nearly "any other" programming language.

The more I have read about parser/compiler writing and used Lisp to write "mini-languages", the more I have started to think of problems in terms of symbolic language transformations, and evaluations of data structures. From here it's just a small step to start wanting a little ad hoc Scheme interpreter in the guts of most of your projects... Greenspun's Tenth Rule :)

All of the same ideas apply just as well in CL of course, it's just that it's just a bit more of a beast to use.

---

### Post by Jesdisciple on 2010-05-02
[http://jesdisciple.blogspot.com/2010/05/learning-lisp.html](http://jesdisciple.blogspot.com/2010/05/learning-lisp.html) :D

---

### Post by mmix on 2010-05-02
arc is written in scheme.
[http://arclanguage.org/](http://arclanguage.org/)

[http://en.wikipedia.org/wiki/Arc_%28programming_language%29](http://en.wikipedia.org/wiki/Arc_%28programming_language%29)

---

