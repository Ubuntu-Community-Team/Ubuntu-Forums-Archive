---
title: "Scheme File IO"
date: 2009-01-26
forum: Programming Talk
---

### Post by Mr.Macdonald on 2009-01-26
I have written the function

```
(define (write-string str sink)
  (define (write str-list)
    (cond ((null? str-list) (write-char #\nl sink))
	  (else (write-char (car str-list) sink)
		(write (cdr str-list)))))
  (write (string->list str)))
```

The problem is that in always prints a newline at the end. But If I don't print it, then when I write to stdout, nothing prints? What else could I write

heres the std's definitions
```
(define stdin
  (open-input-file "/dev/stdin"))
(define stdout
  (open-output-file "/dev/stdout"))
```

---

