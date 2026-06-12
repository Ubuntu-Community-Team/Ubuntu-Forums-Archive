---
title: "Calculation of log of large numbers in C++"
date: 2009-10-21
forum: Programming Talk
---

### Post by Abhishek4563 on 2009-10-21
Hello
I would like to know is there a way to compute logs of 80-digit integers on C++ ? If not then I would like to know if there are codes (c++) for doing the same. Also can double or float data type hold such large integers ? And are there any overheads(in terms of computation time) of using double instead of float ?? I believe float is single precision. I read that double can hold upto 10^308 or so but having only 64-bits I am not sure how is it done (or even that this is true). 
Thanx
Abhishek Tiwari

---

### Post by Tony Flury on 2009-10-21
80 digits is too big for double or floats as far as i know - a C++ expert will confirm that.

Let me qualify that - you can store a number of the order of 10^80 in a double, but it wont be precise - i.e. you wont be able to output all 80 characters of the number. Doubles and floats store their numbers as Mantisaa and Exponent form - for instance : 

12345678901234567890 could well be stored as 1234567 x 10^13 - as you can see it is not precise - but it is probably good enough.

If you have to use precise calculations on big numbers, then i am sure there BigNumber libraries available that can deal with big Integers etc.

Since you want to take the Log of an 80 digit number, do you want the log accurate to 80 decimal places ? If so i would intrigued to know why ? If you don't need the log accurate to 80 decimal places, then you probably don't need to handle your number that accurately either.

---

### Post by Abhishek4563 on 2009-10-21
> **Tony Flury said:**
> 
Since you want to take the Log of an 80 digit number, do you want the log accurate to 80 decimal places ? If so i would intrigued to know why ? If you don't need the log accurate to 80 decimal places, then you probably don't need to handle your number that accurately either.
I am definitely going to use float or double for storing the log. In light of this please suggest me is there need for any additional code for calculating log. To be more precise: I am using GMP for manipulating large numbers , I generate a large number in the code which is stored as a GMP integer but can be converted to double using mpz_get_d() (mpz = gmp integer ; get_d = get double). I was thinking of using this double value and calculating log using the standard log function in C++ . Additionally how should I analyze the error due to this rounding off?
Thanx

---

### Post by MadCow108 on 2009-10-21
gmp should have a logarithm function to calculate it
if not change the library
cln has one:
[http://www.ginac.de/CLN/cln_4.html#SEC29](http://www.ginac.de/CLN/cln_4.html#SEC29)

doubles can hold values up to ~10^3XX. but the precision is only around 15 digits. The rest of the number is stored as the exponent. (all numbers with out waranty! look them up if it is important)

---

### Post by Abhishek4563 on 2009-10-21
> **MadCow108 said:**
> gmp should have a logarithm function to calculate it
if not change the library
cln has one:
[http://www.ginac.de/CLN/cln_4.html#SEC29](http://www.ginac.de/CLN/cln_4.html#SEC29)

doubles can hold values up to ~10^3XX. but the precision is only around 15 digits. The rest of the number is stored as the exponent. (all numbers with out waranty! look them up if it is important)
Unfortunately changing the library is not an option now because I would have to modify a large amount of code and learn the new library too. Though may be I could just use the log function of CLN. But the first I need to be sure that it is of any use as I am going to store the result as double or float. Also please consider my other query regarding overheads of using double over float (Yes I am being toooo fussy but the number of calclulations I am going to do is very very large too)
Thanx

---

### Post by MadCow108 on 2009-10-21
if you are concerned about the overhead double/float you definitely should not use arbitrary precision number libraries.
The overhead by arbitrary precision is many many orders of magnitude greater than float/double.

generally double is as fast as float (internal cpu representation is identical on many architectures) but if the memory bandwidth consumption is twice as big.
So only in the case of memory bandwidth being the bottleneck, they differ in speed.
(and in 99.999999% of cases this difference is completely irrelevant, or outweighed by the better precision)

@your log problem:
it seems gmp does not have a log function. But you could implement yourself with the available functions:
[http://gmplib.org/manual/Float-Arithmetic.html#Float-Arithmetic](http://gmplib.org/manual/Float-Arithmetic.html#Float-Arithmetic)
[http://en.wikipedia.org/wiki/Logarithm#Computers](http://en.wikipedia.org/wiki/Logarithm#Computers)

out of interest: for what do you need that high precision?

---

### Post by Abhishek4563 on 2009-10-21
> **MadCow108 said:**
> 

out of interest: for what do you need that high precision?
Actually you have already solved a lot of my problems. I am implementing the quadratic sieve for factoring 80 digit integers. During the sieve phase I have a an array of about 100000 elements and there and I have to 
traverse it about 10000 times adding log at appropriate places. The reference I am using states that single precision is enough for log values but considering the fact that those were the good old days(late 80s) when I dont think they even had 32- bit processors or atleast they were not as efficient in floating point calculations as today's maybe using double wont have much of an computation overhead compared to the precision you get.

---

### Post by MadCow108 on 2009-10-21
[QUOTE=Donald Knuth]premature optimization is the root of all evil[/QUOTE]

comparing performance of double and float is such an optimization.
Its a waste of time and can induce other errors (e.g. rounding errors) which are not worth an 0.05% increase in speed.

Write your program. if it works see if its fast enough.
Only if not profile it and see where the bottlenecks are and optimize those (by better algorithms or data structures!)
Never optimize without profiling. Most programmers tend to be very bad at guessing the bottlenecks.

---

### Post by Abhishek4563 on 2009-10-21
> **MadCow108 said:**
> comparing performance of double and float is such an optimization.
Its a waste of time and can induce other errors (e.g. rounding errors) which are not worth an 0.05% increase in speed.

Write your program. if it works see if its fast enough.
Only if not profile it and see where the bottlenecks are and optimize those (by better algorithms or data structures!)
Never optimize without profiling. Most programmers tend to be very bad at guessing the bottlenecks.
Thanx Will keep that in mind

---

