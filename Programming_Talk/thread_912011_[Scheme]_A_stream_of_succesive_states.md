---
title: "[Scheme] A stream of succesive states"
date: 2008-09-06
forum: Programming Talk
---

### Post by nvteighen on 2008-09-06
Ok, I definitely need a bit help here. Possibly, my mistake comes from not understanding how bindings work...

For a little project I have, I want to write a stream of succesive states for a certain data. In this case, scores. As scores have to be defined from "external" data, I thought in a solution like this:

```

(define (make-score init)
  (cons-stream init
               (lambda (x)
                 (make-score x))))

```

But, though that works for an initial setting, say by:
```

(define my-score (make-score 0))
((stream-cdr my-score) 9)

```
The stream won't grow further and any attempt to do (stream-cdr my-score) will, obviously fail and not yield the 9 that was passed as argument.

I know using assignment would solve this, but I'd like to use that only as last resort. Is there a pure-functional way to create a  lazy list giving a formal parameter so that scores are recorded as:
(0 1 21 53 2 . [promise])?

Thanks!

P.S.: I was also wondering if maybe an "inverted stream" implemented like:
```

(define (cons-inv-stream x y)
  ((delay x) y))

```
could work for this?

---

