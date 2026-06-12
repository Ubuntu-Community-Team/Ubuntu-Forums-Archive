---
title: "SICP - Iterative vs. Looping"
date: 2005-12-18
forum: Programming Talk
---

### Post by darthsabbath on 2005-12-18
Hi, all,

I'm working through "The Structure And Interpretation of Computer Programs", and... wow... heavy stuff.  But I had a question on something that's a bit confusing, and I was hoping someone who's read it may have some insight.  In Section 1.2.1, it goes into Linear Recursion and Iteration, and it has some (at least from what I consider) disparaging remarks on the idea of loop constructsfrom other languages such as for, while, etc, instead seeming to prefer what it calls an iterative process... for example:

(define (factorial n)
  (fact-iter 1 1 n))

(define (fact-iter product counter max-count)
  (if (> counter max-count)
      product
      (fact-iter (* counter product)
                 (+ counter 1)
                 max-count)))

While at heart it seems that the two are the same, but I was wondering, in a non-Lisp based language such as Python or C, would there be any advantage to using an example such as that listed above compared to a for or while statement?  I fail to see the point, unless I'm completely missing something or haven't gotten far enough into the book.  It merely calls loops "syntactic sugar." 

Phil

---

### Post by tbrownaw on 2005-12-18
[QUOTE=darthsabbath]While at heart it seems that the two are the same, but I was wondering, in a non-Lisp based language such as Python or C, would there be any advantage to using an example such as that listed above compared to a for or while statement?  I fail to see the point, unless I'm completely missing something or haven't gotten far enough into the book.  It merely calls loops "syntactic sugar." [/QUOTE]
There is no point.

Really, it's the difference between "factorial of *n* is n times factorial of *n*-1, and factorial of 1 is 1" and "factorial of *n* is the product of all numbers from 1 to *n*". Just a different way of thinking about things -- dealing with high-level math concepts vs. thinking through the practical results of those concepts. The author's personal opinion is apparently to favor the former.

---

### Post by LordHunter317 on 2005-12-18
[QUOTE=darthsabbath]While at heart it seems that the two are the same, but I was wondering, in a non-Lisp based language such as Python or C, would there be any advantage to using an example such as that listed above compared to a for or while statement?[/quote]It's frequently clearer to express the algorithm in this iterative recursive manner than it is in an interative loop.

Not always.  I should also point out that there's a clear distinction between a recursive and iterative definition (i.e., you can define the factorial of n in both ways) and a recursive and iterative implementation (i.e., you can write a program to solve it both ways, regardless of the definition).  It should also be noted that in some situations, one definition is clearly prefered and one implementation is clearly prefered, and they may not always be the same.

> It merely calls loops "syntactic sugar." They are short-hand for an iterative process.  That's not to say they're useful shorthand, but they're shorthand nonetheless.

---

