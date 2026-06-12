---
title: "SICP task 1.3"
date: 2009-07-09
forum: Programming Talk
---

### Post by cdiem on 2009-07-09
Since a few days I've been trying to learn scheme... but it seems very diferent from what I'm used to. I have stuck with the exercise 1.3 from the SICP -> finding the sum of squares of the two higher numbers given 3.
Here's what I have:

[PHP](define (square x) (* x x))

(define (findBigger x y) (cond ((> x y) x)
                               ((< x y) y)))

(define (findSmaller x y) (cond ((> y x) x)
                               ((< y x) y)))

(define (sumSquaresTwoHighest a b c) 
  (+ square(findBigger a b) square(findBigger(c findSmaller(a b)))))[/PHP]

But for some reason it keeps telling me, that "procedure application: expected procedure, given: 3; arguments were: 4". I can't seem to understand what is wrong here..

---

### Post by baizon on 2009-07-09
Your brackets are wrong :)  
```

(define (square x) (* x x))

(define (findBigger x y) (if (> x y) x y))

(define (findSmaller x y) (if (> y x) x y))

(define (sumSquaresTwoHighest a b c) 
  (+ (square(findBigger a b)) (square (findBigger c (findSmaller a b)))))  

```

Check [http://en.wikipedia.org/wiki/Prefix_notation]("http://en.wikipedia.org/wiki/Prefix_notation")

---

### Post by cdiem on 2009-07-09
That worked; I thought I have tried all types of combinations for parentheses before asking here; the article explained it fine. Thanks a lot!

---

### Post by CptPicard on 2009-07-09
Your indentation style is also a little bit strange, but you'll figure out the "usual" way of doing things in due time. In general, what you're doing is that you're nesting S-expression lists of the form (function x y..), and a substantial subexpression that needs to stand out on its own is often laid out on its own rows and indented so it is visually distinct...

---

### Post by nvteighen on 2009-07-09
> **cdiem said:**
> That worked; I thought I have tried all types of combinations for parentheses before asking here; the article explained it fine. Thanks a lot!

Lisp syntax is:
```

(*procedure* *args...*)

```

Always (well, except when some macro comes in play... or seen the other way, when something doesn't follow that then it is a macro)

---

