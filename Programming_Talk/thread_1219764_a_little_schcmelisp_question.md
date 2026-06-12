---
title: "a little schcme/lisp question"
date: 2009-07-22
forum: Programming Talk
---

### Post by akimatsu123 on 2009-07-22
hi, i was reading "Structure and Interpretation of Computer Programs" from MIT Press online, and I came across this in the starting chapters. 

In scheme/lisp, how is:

(define (new-if predicate then-clause else-clause)
   (cond (predicate then-clause)
         (else else-clause) ))

different from the actual if conditional statement?

---

### Post by Paul Miller on 2009-07-22
The cond special form evaluates the conditionals lazily.  Your new-if function has to evaluate predicate, then-clause, and else-clause every time, even if (for instance) the predicate is true.

---

### Post by nvteighen on 2009-07-22
You can implement if this way, by just know a bit of boolean logics:

```

(define (my-if if-clause then-clause else-clause)
  (or (and if-clause
           then-clause)
      else-clause))

```

Try it and it works :) The implementation of the optional else-clause would require a modification based on recursion (calling my-if again inside itself :))

---

### Post by nvteighen on 2009-07-22
> **Paul Miller said:**
> The cond special form evaluates the conditionals lazily.  Your new-if function has to evaluate predicate, then-clause, and else-clause every time, even if (for instance) the predicate is true.

No, cond is a macro that expands to a series of ifs... There's no laziness there, but two stages of execution: the macro-expansion and the execution of the expanded code.

Sadly, SICP doesn't get into macros... :(

---

### Post by nmaster on 2009-07-22
new-if uses applicative order of evaluation so both the 'then' and the 'else' clauses are evaluated regardless of the predicate value.  try using new-if in a recursive procedure.

(define (squares numlst)
    (new-if (null? numlist) (list)  (cons (square (car numlst)) (squares (cdr numlst)))))

This will create an error whereas the following will not.

(define (squares numlst)
   (if (null? numlist)
        (list)
        (cons (square (car numlst))
                 (squares (cdr numlst)))))


This exercise is supposed to get you to think about how applicative order of evaluation works.




NOTE: (define square (lambda (x) (* x x)))

---

### Post by nmaster on 2009-07-22
SICP is really a great book, but its not easy.  I would highly suggest using some resources from Berkeley. [http://inst.eecs.berkeley.edu/~cs61a/sp09/]("http://inst.eecs.berkeley.edu/%7Ecs61a/sp09/")


this wiki has some good answers too. [http://sicp.org.ua/sicp](http://sicp.org.ua/sicp)

---

### Post by CptPicard on 2009-07-22
> **nvteighen said:**
> No, cond is a macro that expands to a series of ifs... There's no laziness there

Well, there is... in the if. :) Interestingly the lazy-branches if is one of the few special cases that must be built into the language -- all the rest can be built with macros and such.

History trivia -- the if was originally invented in Lisp in the form of the original "cond" which was defined in this kind of lazy fashion to enable braching.

---

### Post by akimatsu123 on 2009-07-23
> **neal.m.master said:**
> new-if uses applicative order of evaluation so both the 'then' and the 'else' clauses are evaluated regardless of the predicate value.  try using new-if in a recursive procedure.

Oh, of course i understand now. If used in a recursion then the function will go on forever because applicative order evaluates the arguments first.

---

### Post by nmaster on 2009-07-23
> **akimatsu123 said:**
> Oh, of course i understand now. If used in a recursion then the function will go on forever because applicative order evaluates the arguments first.

Exactly.  Later in SICP (chapter 4 I think), you'll learn more about evaluators.  You'll be able to write a metacircular lisp evaluator that uses normal order.  The Berkeley link I posted probably already has this code (I forget what Prof. Harvey provides) and the difference between normal and applicative order will be very clear.

---

