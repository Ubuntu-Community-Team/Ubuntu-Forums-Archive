---
title: "SICP Exercise 1.5"
date: 2010-01-14
forum: Programming Talk
---

### Post by badperson on 2010-01-14
Hi,
I'm starting to work thru the SICP book, and I was curious about one of the exercies. (I'm working through the book on my own, not taking a class)

> Exercise 1.5.  Ben Bitdiddle has invented a test to determine whether the interpreter he is faced with is using applicative-order evaluation or normal-order evaluation. He defines the following two procedures:

(define (p) (p))

(define (test x y)
  (if (= x 0)
      0
      y))

Then he evaluates the expression

(test 0 (p))

What behavior will Ben observe with an interpreter that uses applicative-order evaluation? What behavior will he observe with an interpreter that uses normal-order evaluation? Explain your answer. (Assume that the evaluation rule for the special form if is the same whether the interpreter is using normal or applicative order: The predicate expression is evaluated first, and the result determines whether to evaluate the consequent or the alternative expression.) 

my answer to this is that, a) the procedure p recursively calls itself and enters an infinite loop and b) normal-order evaluation calls procedures only as they are needed; so in the procedure test, once it sees x is 0, it returns 0, whereas with applicative-order evaluation the procedures will be evaluated beforehand, so it enters the infinite loop...

does that sound right? Just want to make sure I'm on solid ground here, because I have a feeling an intuitive understanding of this issue will be important as the book progresses. 
thanks, 
bp

---

### Post by nvteighen on 2010-01-14
> **badperson said:**
> Hi,
I'm starting to work thru the SICP book, and I was curious about one of the exercies. (I'm working through the book on my own, not taking a class)



my answer to this is that, a) the procedure p recursively calls itself and enters an infinite loop and b) normal-order evaluation calls procedures only as they are needed; so in the procedure test, once it sees x is 0, it returns 0, whereas with applicative-order evaluation the procedures will be evaluated beforehand, so it enters the infinite loop...

does that sound right? Just want to make sure I'm on solid ground here, because I have a feeling an intuitive understanding of this issue will be important as the book progresses. 
thanks, 
bp

You're right :)

---

