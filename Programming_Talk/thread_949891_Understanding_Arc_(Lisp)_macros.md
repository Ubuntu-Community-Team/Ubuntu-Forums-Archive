---
title: "Understanding Arc (Lisp) macros"
date: 2008-10-16
forum: Programming Talk
---

### Post by Nemooo on 2008-10-16
Well, I've been playing around with [Arc]("http://arclanguage.org") for a while and have now reached the point where I'd like to play with macros.

I made this little program for the second Euler problem:
```
; (fibonacci max) returns the sum of all the even-valued terms in the Fibonacci
; sequence which do not exceed max.
; Used for Project Euler - Problem 2.

(def fibonacci (max)
  (with (x 1 y 1 z 0 sum 0)
    (while (< (and x y z) (- max (and x y z)))
      (= z (+ x y))
      (if (even z) (zap [+ _ z] sum))
      (= x (+ y z))
      (if (even x) (zap [+ _ x] sum))
      (= y (+ z x))
      (if (even y) (zap [+ _ y] sum)))
    sum))
```

Since the code is a little repetitive, I thought I'd write a macro to shorten the code (and to try macros out in general):

```
(def fib-test (max)
  (with (x 1 y 1 z 0 sum 0)
    (while (< (and x y z) (- max (and x y z)))
      (sum-up z '(x y))
      (sum-up x '(y z))
      (sum-up y '(z x)))
    sum))

(mac sum-up (arg-1 . body)
  `(= arg-1 (+ ,@body))
  `(if (even ,arg-1) (zap [+ _ ,arg-1] sum)))
```

When I evaluate the macro line by line I get the desired output:
```
>>> (with (arg-1 2 body '(2 3)) `(= arg-1 (+ ,@body)))
(= arg-1 (+ 2 3))
>>> (with (arg-1 2 sum 1) `(if (even ,arg-1) (zap [+ _ ,arg-1] sum)))
(if (even 2) (zap (fn (_) (+ _ 2)) sum))
```

But when I run the code as posted above it gives me the following message: Error: Function call on inappropriate object #3(tagged mac #<procedure>) (0 (x y . nil))

Arc macros are described [here]("http://ycombinator.com/arc/tut.txt").

---

