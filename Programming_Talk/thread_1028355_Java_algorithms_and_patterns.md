---
title: "Java algorithms and patterns"
date: 2009-01-02
forum: Programming Talk
---

### Post by cjnkns on 2009-01-02
Hi all - 

Mainly (for work) spend my day programming java web apps.

I am at a disadvantage because I am very weak when it comes to algorithms and patterns. I was hoping the community here could provide some good ideas for learning resources.

I have a patterns book at home - I think it's the Head First series. Don't really have any algorithm material yet though.

Any ideas and help would be great! 

Thanks and Happy New year to everyone.

---

### Post by Delever on 2009-01-02
Hmm, maybe try some project which requires more complicated algorithms?

---

### Post by escapee on 2009-01-02
Though somewhat difficult to read unless you are very math and proof oriented, the CLRS "Introduction to Algorithms" book is VERY comprehensive in many different types of algorithms.

---

### Post by CptPicard on 2009-01-02
Well... it is my experience that especially the patterns part really only comes from programming. You can learn literature but the really educational part is both coding yourself and reading other people's code.

Algorithms should be learned in a language-independent fashion, doing implementations is a "homework assignment". I am not a huge fan of "Algorithms in language X" style books -- pages and pages of verbose implementation as in Java does not get to the meat of the stuff fast enough.

You may want to get a copy of Leiserson, Cormen, Rivest, Stein: Introduction to Algorithms. Don't get bogged down in the math analysis parts (excluding a general understanding of big-Oh notation and analysis) if you don't need them as a CS student -- read the pseudocode, understand the structures and algorithms and know when to use which.

A typical data structures undergrad course goes far... and it goes something like this:

Arrays, stacks, lists, hashes, trees, some balanced tree structure, sorting algorithms, graphs.

In the Gang of Four lingo, some of the most important patterns for OOP are Visitor, Composite, Strategy, Delegate (the last tree are similar), Facade. Learn to use callbacks. Java's anonymous inner classes are very powerful. 

An interesting point to note is that data structures and algorithms have a certain duality -- data structures are parts of algorithms "reified" in RAM for later use, really. The more experience I gain, the more I see how a lot of stuff are just different sides of the same coin, viewed a bit differently... :)

---

### Post by CptPicard on 2009-01-02
> **escapee said:**
> Though somewhat difficult to read unless you are very math and proof oriented, the CLRS "Introduction to Algorithms" book is VERY comprehensive in many different types of algorithms.

Hey, CLRS is actually really easy as far as textbooks go ;) It's a good *introduction* to mathematical treatment and really holds your hand in being verbose if you're not mathematically oriented.

---

