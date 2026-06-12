---
title: "Very simple LISP question"
date: 2010-07-10
forum: Programming Talk
---

### Post by yanollego on 2010-07-10
```
(define (abs x)
   (if (< x 0)
       (-x)
       x))
;Value: abs

abs 7
;Value: 7

g
;Value: -2

abs g
;Value: -2
```Why is it not working properly?
I am using MIT/GNU Scheme.

---

### Post by soltanis on 2010-07-10
This is why I hate Scheme -- hard to find proper documentation on it.

...okay, I found out that I had sigscheme installed but it took me like 5 minutes to figure out how to run it  ("sscm"). I **really** hate scheme now.

Okay, so I think your problem is this:

```

(-x)

```

Unlike in an imperative language, that does not mean "negate x". In fact, that line crashes my sigscheme interpreter (man, this interpreter really sucks) with an "ill formatted number" error.

Instead, you should use the "-" function with a single argument:

```

(- x)

```

Believe it or not, they do have two different meanings. In my interpreter, that does mean "negate x" (it's supposedly an R5RS interpreter by the way).

---

### Post by yanollego on 2010-07-10
New code, still not working. Puzzled.

```
g
;Value: -2

(define (abs x)
   (cond ((< x 0) (- x))
         ((= x 0) (0))
         ((> x 0) (x))))
;Value: abs

abs g
;Value: -2

(- g)
;Value: 2
```

---

### Post by crush304 on 2010-07-10
(abs g)

---

### Post by yanollego on 2010-07-10
crush, in Lisp you do not put numbers into round brackets to evaluate them...
The problem is elsewhere....

---

### Post by nvteighen on 2010-07-11
**Everytime** you want to apply a function to some arguments you use the following syntax:

```

(function arg0 arg1 ...)

```

So, use:
```

(abs -2)

```

Without parentheses, Scheme will just output the values... or actually, only the last value: in your case, the number itself without further evaluation.

I recommend you to look at the SICP videos ([http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/](http://groups.csail.mit.edu/mac/classes/6.001/abelson-sussman-lectures/))

---

