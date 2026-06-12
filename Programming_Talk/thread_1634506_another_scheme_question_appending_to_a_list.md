---
title: "another scheme question: appending to a list"
date: 2010-11-30
forum: Programming Talk
---

### Post by badperson on 2010-11-30
Hi,
I'm trying to write the following routine that will return a list of prime factors, e.g., 24 = 2 * 2 * 2 * 3. 

I have the basic method where it should work but I'm getting an error with the line that tries to append to the list: 
```
(define (getPrimeFactors num)

;; 1) start with 2, if x is divisible by 2, add 2 to the list. x becomes x/2, and
(define (getPrimeFactorsIteration num divisor primes)
  (cond
   ((= 1 num) primes)
   
   ((not (isPrime? divisor)) (getPrimeFactorsIteration num (+ 1 divisor) primes))
   ((and (isPrime? divisor) (= (remainder num divisor) 0)) 
    ;; add divisor to primes, then new iteration
    
    (getPrimeFactorsIteration (/ num divisor) 2 (append primes divisor)))))
(getPrimeFactorsIteration num 2 '())

)

```


when running in emacs I get this error: 

> ;The object 2, passed as an argument to append, is not a list.
;To continue, call RESTART with an option number:
; (RESTART 2) => Return to read-eval-print level 2.
; (RESTART 1) => Return to read-eval-print level 1.

I tried adding a number to a list with the same basic syntax....
```
efine testlist '(1 2 3))
(define num 4)


 (append testlist 4)

;Value 13: (1 2 3 . 4)


```


any ideas?
bp

---

### Post by NovaAesa on 2010-11-30
Instead of
```
(append primes divisor)
```
you could instead put
```
(append primes (list divisor))
```
or
```
(cons divisor primes)
```

Note that this is all from memory, I haven't coded in Scheme for a while and don't have it installed at the moment.

---

### Post by Arndt on 2010-12-01
> **badperson said:**
> Hi,
I'm trying to write the following routine that will return a list of prime factors, e.g., 24 = 2 * 2 * 2 * 3. 

I have the basic method where it should work but I'm getting an error with the line that tries to append to the list: 
```
(define (getPrimeFactors num)

;; 1) start with 2, if x is divisible by 2, add 2 to the list. x becomes x/2, and
(define (getPrimeFactorsIteration num divisor primes)
  (cond
   ((= 1 num) primes)
   
   ((not (isPrime? divisor)) (getPrimeFactorsIteration num (+ 1 divisor) primes))
   ((and (isPrime? divisor) (= (remainder num divisor) 0)) 
    ;; add divisor to primes, then new iteration
    
    (getPrimeFactorsIteration (/ num divisor) 2 (append primes divisor)))))
(getPrimeFactorsIteration num 2 '())

)

```


when running in emacs I get this error: 



I tried adding a number to a list with the same basic syntax....
```
efine testlist '(1 2 3))
(define num 4)


 (append testlist 4)

;Value 13: (1 2 3 . 4)


```


any ideas?
bp

Do you know how lists work in Lisp/Scheme? They are pairs A.B, with A being the first element in the list, and B being the rest of list. B is typically a list itself (ultimately the empty list ()), but it may be something else, for example 4, and then you get what you got above, an "improper" list (1 2 3 . 4). Trying to do normal list operations on such improper lists, for example another append, will fail.

If you stick to lists when using 'append', nothing strange will happen. So don't append (1 2 3) and 4, append (1 2 3) and (4) instead. That will yield the proper list (1 2 3 4).

You construct a list pair with the function 'cons', so if you want to put an element first in a list, you can put it there like this: (cons 4 '(1 2 3)) => (4 1 2 3).

---

### Post by badperson on 2010-12-03
thanks for the replies...

I've tried two solutions suggested here:
```
(cons primes divisor)
;; and
(append primes(list divisor))

```

and both return the error...
> ;Unspecified return value

as to the question above...I'm learning how lists work in scheme...slowly:D I actually had thought that cons was more like a map...so I need to do some more reading. 

the code is now the same as above with the exception of this:
```
   ((and (isPrime? divisor) (= (remainder num divisor) 0)) 
    ;; add divisor to primes, then new iteration
    (getPrimeFactorsIteration (/ num divisor) 2 (cons primes divisor)))))
```


thanks, 
bp

---

