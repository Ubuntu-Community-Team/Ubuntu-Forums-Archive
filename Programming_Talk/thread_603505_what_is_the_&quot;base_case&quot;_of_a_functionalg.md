---
title: "what is the &quot;base case&quot; of a function/algorithm?"
date: 2007-11-05
forum: Programming Talk
---

### Post by nite owl on 2007-11-05
Hi came across a question from past papers I have been looking at preparing for exams.I am totally stumped as to what this is...

Gives me a procedure, then asks:  what constitutes the base case in this procedure? I would post the procedure, except its in a pdf format that you can not copy and paste.

---

### Post by bunker on 2007-11-05
Is it looking for a best case on the problem or on an algorithm?  The former case is rather difficult, but best case of the algorithm is a bit easier -- you need to use omega notation.  Wikipedia has some decent info: [http://en.wikipedia.org/wiki/Big_O_notation](http://en.wikipedia.org/wiki/Big_O_notation)

Basically what you need to do is approximate each part of the procedure and decide in the best possible case, what is the minimum number of times it will happen.  So, say for a linear search of a list the best case is omega(1), when the first item in the list is the target you're looking for.

---

### Post by CptPicard on 2007-11-05
The "base case" would be the "trivial, obvious case" of a function, and in particular in recursion, the termination condition (which often is trivial, just returning some particular value).

---

