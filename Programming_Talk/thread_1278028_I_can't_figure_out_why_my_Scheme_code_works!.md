---
title: "I can't figure out why my Scheme code works!"
date: 2009-09-29
forum: Programming Talk
---

### Post by manualqr on 2009-09-29
some background:
In our post-AP comp-sci class in high school, our teacher is (re)-exposing us to PLT scheme. I had an aversion towards it in the past because we were only allowed to use the "Beginning Student" language. But after trying 'real' scheme - my mind is being blown away!

We're following Kathi Fisler's (WPI) course on scheme and we just got to macros ([http://web.cs.wpi.edu/~cs1102/a08/Assignments/Hwk6/index.html](http://web.cs.wpi.edu/~cs1102/a08/Assignments/Hwk6/index.html)). The solution to the dillo problem is a pretty in-efficient macro, imo. It does a O(n) lookup every time you want send a message to a class.

I was trying to figure out a better solution using hash-tables and something really odd happened: it worked. Take a look;
```

(define-syntax class
  (syntax-rules (: @)
    [(_
      (: field ...)
      (@ func (arg ...) body)
      ...)
     
     (lambda (field ...)
       (let ((val-mat (make-hash)))
         (hash-set! val-mat func (lambda (arg ...) body))
         ...
         (lambda (msg)
           (hash-ref val-mat msg))))]))

(define-syntax def-obj
  (syntax-rules ()
    [(_ name (field ...))
     (define name
       (class
         (: field ...)
         (@ (string->symbol (string-append "get-" (symbol->string 'field))) () field)
         ...))]))

(define-syntax call
  (syntax-rules ()
    [(_ obj sym)
     ((obj 'sym))]
    [(_ obj sym (arg ...))
     ((obj 'sym) arg ...)]))

```
(def-obj and call are un-related, they just make using class easier)

I was expecting an error in 'class', around the let binding.. I'm returning a lambda with a reference to val-mat, which is inside the let. So, how is this working (i.e working with val-mat)?;
```

> (def-obj post (auth date))
> (define help! (post "mq" 2009))
> (call help! get-auth)
"mq"
> (call help! get-date)
2009

```

---

### Post by nvteighen on 2009-09-29
Because you're enclosing val-mat into a closure :) lambdas do that: they catch stuff and preserve their references.

What you've done is roughly how actually Scheme OOP systems like MIT/GNU SOS or TinyCLOS work.

---

