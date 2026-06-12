---
title: "You have got to read this!!!1!!1!!!1oneone"
date: 2007-02-06
forum: Programming Talk
---

### Post by spazo on 2007-02-06
anyway now that I attracted you to my message ive got to tell you all something! ok so im in algebra 2 and theres this one problem and our teacher just said to round on it. So being me I didnt round. well I came up with this really big decimal number so i tell the calculator to swich it to fraction so its easyer to work with. Well it cant... so I got to my computer and and punch it in the computer calc well it cant eather(well the form I want it in). so im like scew this ill just make a quick program. anyway I finish the program only like a 25 line program, I run it, the computer crashes. and the I realise I might want to change the varibles to use more memory. so I change the statement from "int" to "float". Well guess what no luck. so I change it to "long double". It took about 5 sec to run it after it compiled it. Im thinking to myself "holy crap my dual core 3ghz 1gig mem. computer is taking this long for 25 lines of code!" well it finishes I write the number down (4 sheets of paper!:lolflag: ) and im gunna turn it in. just wanted to tell you guys. If you did something like this feel free to post!

---

### Post by hod139 on 2007-02-06
What's really amazing is that you will find out there are numbers that **can't** be represented as a fraction, these are so called irrational numbers.  The numbers after the decimal  point continue forever without any pattern or repetition.  The common examples are PI(3.1414...), e(2.7182...), or sqrt(2).  

Also, don't trust the computer's results too much with floating point math. Computers have finite precision and are actually doing some rounding too.

---

### Post by daniel of sarnia on 2007-02-06
> **hod139 said:**
> 
Also, don't trust the computer's results too much with floating point math. Computers have finite precision and are actually doing some rounding too.

That's what "c++ in 21 days" book tells me

edit: this may be a job for math lib!!

---

### Post by xtacocorex on 2007-02-06
If you use FORTRAN, you can easily set the precision of real values:
```

REAL :: myvar  ! Single Precision (also can use REAL(KIND=4)
REAL(KIND=8) :: myvar2  ! Double Precision
REAL(KIND=16) :: myvar3 ! Triple Precision
REAL(KIND=32) :: myvar4 ! Quadruple Precision

```
I haven't used anything greater than double precision, in my world, that's enough precision to give accurate results.  There will be roundoff, but FORTRAN is a language made for math and does it the best (IMO).

As hod139 said, you might have run into an irrational number and won't get a fraction.  You may be able to get an approximate fraction, PI is approximately 22/7.  In all my codes, I define PI as 4.0*ATAN(1.0), where ATAN is in the arctangent.  This is getting off topic, so sorry for that.

---

### Post by hod139 on 2007-02-07
> **xtacocorex said:**
> If you use FORTRAN, you can easily set the precision of real values:

Floating point error is language agnostic.  Instead of explaining floating point in this thread I will simply refer you to [What every computer scientist should know about floating-point arithmetic]("http://docs.sun.com/source/806-3568/ncg_goldberg.html")

> 
 In all my codes, I define PI as 4.0*ATAN(1.0), where ATAN is in the arctangent.
Why not just define it as 
3.1415926535897932384626433832795029

---

### Post by LotsOfPhil on 2007-02-07
> **hod139 said:**
> What's really amazing is that you will find out there are numbers that **can't** be represented as a fraction, these are so called irrational numbers.  The numbers after the decimal  point continue forever without any pattern or repetition.  The common examples are PI(3.1414...), e(2.7182...), or sqrt(2).  

Also, don't trust the computer's results too much with floating point math. Computers have finite precision and are actually doing some rounding too.

The original poster mentioned being in math class. Given that I don't think we should lump pi and sqrt(2) together.

pi, e and sqrt(2) are irrational, but sqrt(2) is algebraic whereas the other two are transcendental.  :D

---

### Post by g3k0 on 2007-02-07
.1 + .1 + .1 + .1 + .1 + .1 + .1 + .1 + .1 + .1 != 1 on a computer =)
Good luck with your decimal.

---

### Post by sympeltun on 2007-02-15
> **g3k0 said:**
> .1 + .1 + .1 + .1 + .1 + .1 + .1 + .1 + .1 + .1 != 1 on a computer =)
Good luck with your decimal.

lol thats funny..

double precision can be a little unpredictable and unexpected to someone that's not aware on how to avoid it.. (i know i cant lol)

good luck

---

