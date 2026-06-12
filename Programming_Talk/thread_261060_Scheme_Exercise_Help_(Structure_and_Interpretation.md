---
title: "Scheme Exercise Help (Structure and Interpretation book)"
date: 2006-09-19
forum: Programming Talk
---

### Post by Revert on 2006-09-19
I've been working through the Structure and Interpretation of Computer Programs book and have hit a bit of a problem. Since I chose to use this book as part of my curriculum, my teacher doesn't actually know much of anything about Lisp or its varients, so I was hoping to get a bit of help.

The problem is:

> Exercise 1.11. A function f is defined by the rule that f(n) = n if n<3> 3. Write a procedure that computes f by means of a recursive process. Write a procedure that computes f by means of an iterative process.


I have no trouble writing a recursive procedure/recursive process, but I am having trouble writing it iteratively; I'm not familiar enough with Lisp to know how to model this, and I don't know how to do it iteratively with three branching sections. I'm assuming it'd require some sort of running total and a number of variables to save the state, and I was thinking about possibly trying to work from the bottom up, but I'm not real sure.

If anyone can help me with an iterative version, it'd be much appreciated; right now I'm just confused.

---

### Post by toojays on 2006-09-19
For those who don't have the text, the question can be found online at the end of [the section on Tree Recursion](http://mitpress.mit.edu/sicp/full-text/book/book-Z-H-11.html#%_sec_1.2.2).

Revert, I haven't tried the question yet, but it seems to be that correct answer to the exercise will be similar to the fibonaci example, but with three state variables instead of two. Have you tried looking at it along these lines?

---

