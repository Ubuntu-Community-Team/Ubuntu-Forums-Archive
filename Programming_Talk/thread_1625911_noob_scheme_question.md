---
title: "noob scheme question"
date: 2010-11-19
forum: Programming Talk
---

### Post by badperson on 2010-11-19
Hi,
I'm starting to work a bit with scheme, and I'm trying to write a procedure that will determine if a number is prime. This is a very basic, brute force solution to that problem, but I'm having some trouble with the scheme syntax. 

```

(define (isPrime? x)
;; private procedures
  (define (isComposite? i)
    (if (= (remainder x i) 0)
	#t
	#f))

;; this is not defined yet. What this method will for two conditions: 1) if i is less than x-1 and if the remainder of x and i is zero, then it's
;; not a prime number and the return value of isPrime is false. 2) If i = x-1 and isComposite is false, then the number is prime and the return
;; value of isPrime is true. 3) If the previous two conditions are false, then isPrimeIteration recursively calls itself with i+1 as an argument. 
;; what I don't know how to do is have a cond block and have the consequent be return value for the entire method
(define (isPrimeIteration i)
i)

(isPrimeIteration 2)

)
```
bp

---

### Post by hyperAura on 2010-11-19
this looks like school homework.. you should try doing it on your own..

---

### Post by badperson on 2010-11-19
it's not, I promise:)

I'm working my way thru the SICP book on my own...no problem, I'll get to that eventually, the book just started talking about defining private procedures defined in a parent procedure...

I just don't see the equivalent of defining a boolean variable (as in java) and being able to set the value and return the variable when given conditions are met. 
I'm sure I'll come across if eventually...

---

### Post by Arndt on 2010-11-19
> **badperson said:**
> it's not, I promise:)

I'm working my way thru the SICP book on my own...no problem, I'll get to that eventually, the book just started talking about defining private procedures defined in a parent procedure...

I just don't see the equivalent of defining a boolean variable (as in java) and being able to set the value and return the variable when given conditions are met. 
I'm sure I'll come across if eventually...

So what problem with the Scheme syntax are you having?

---

### Post by saulgoode on 2010-11-19
```
(define (isPrime? x)
;; private procedures
  (define (isComposite? i)
    (if (= (remainder x i) 0)
	#t
	#f))

;; this is not defined yet. What this method will for two conditions: 
;; 1) if i is less than x-1 and if the remainder of x and i is zero, then it's
;; not a prime number and the return value of isPrime is false. 
;; 2) If i = x-1 and isComposite is false, then the number is prime and the return
;; value of isPrime is true. 
;; 3) If the previous two conditions are false, then isPrimeIteration
;; recursively calls itself with i+1 as an argument. 
;; what I don't know how to do is have a cond block and have the consequent 
;; be return value for the entire method 
```

Start out by implementing exactly what you described. The "return value" is merely whatever the last line executed evaluates to.

```
  (define (isPrimeIteration i)
    (cond 
      ((< i (- x 1))
        (if (zero? (modulo x i))
          #f ) ) ; <== last line executed if these conditions are met
      ((= i (- x 1))
        (if (= (isComposite? i) #f)
          #t ) ) ; <== last line executed if these conditions are met
      (else
        (isPrimeIteration (+ i 1)) ) ) )
  (isPrimeIteration 2) )
```
        
There is a serious problem though. If i=x-1 then *isComposite?* will never evaluate to true and your iteration will never end for prime x's. 
          
I would recommend forgetting about your *isComposite?* function (just test the *modulo* for zero). Focus on the three possibilities for i as it increments each time through the iteration:

```
  (define (isPrimeIteration i)
    (cond 
      ((< i x)
        (if (zero? (modulo x i))
          ; ... what to do if remainder is zero
          ; ... what to do if remainder is non-zero 
          ) )
      ((= i x)
        (if (zero? (modulo x i))
          ; ... what to do if remainder is zero
          ; ... what to do if remainder is non-zero 
          ) )
      (else
        ; ... what to do if i is greater than x
        ) )
  (isPrimeIteration 2) )
```

---

### Post by badperson on 2010-11-26
> The "return value" is merely whatever the last line executed evaluates to.

that's what was tripping me up. The procedure below seems to work:
```
(define (isPrime? x)
;; brute force isPrime procedure. 11/26/10
(define (isPrimeIteration i)
  (cond
   ((= x 1) #t)
    ((= i x) #t)
   ((= (remainder x i) 0) #f)
   (else 
    (isPrimeIteration (+ i 1))))
)
(isPrimeIteration 2)

)
```

thanks

---

