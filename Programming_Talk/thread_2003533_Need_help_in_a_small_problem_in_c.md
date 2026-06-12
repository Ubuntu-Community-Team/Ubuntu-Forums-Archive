---
title: "Need help in a small problem in c"
date: 2012-06-14
forum: Programming Talk
---

### Post by nir2000 on 2012-06-14
Hi everybody!
I need help in writing a small program in c which prints the factorial of small numbers.
I already have a function which tells me if a number is a prime or not and I can use it in my program.
required output of the program should be for example:
9=3x3  
17 is prime
52=2x2x13
and so on...
Please help me to solve that problem.
I thank you in advance.
Nir

---

### Post by Tony Flury on 2012-06-14
sounds like homework to me - but i assume you mean factors (and not factorial).

Think about how you would solve the problem on paper - and come back and ask about a specific piece of code - no-one here will write your code for you.

---

### Post by 11jmb on 2012-06-14
> **Tony Flury said:**
> sounds like homework to me - but i assume you mean factors (and not factorial).

Think about how you would solve the problem on paper - and come back and ask about a specific piece of code - no-one here will write your code for you.

I second this, but I will give you a hint, though. Think about this one recursively. You will keep breaking a number into smaller pieces until you have only prime numbers. This means that you can do the same thing on any number of any size. For example:

```

756 = 2*378
378 = 2*189
189 = 3*63
63 = 3*21
21 = 3*7
7 is prime
21 = 7*3
63 = 7*3*3
189 = 7*3*3*3
378 = 7*3*3*3*2
756 = 7*3*3*3*2*2

```

---

### Post by kingtaurus on 2012-06-14
Read this: [Sieve of Eratosthenes]("http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes")

Check to see if it is prime; if not, use the list of primes and modulo arithmetic.

---

