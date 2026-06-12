---
title: "C and gmp lib for big integers"
date: 2010-03-22
forum: Programming Talk
---

### Post by MilEsSmiLes on 2010-03-22
Hi to everyone..

In java I have used the biginteger class to create with a command called something like propably_prime(size) to create a random integer.

I cant find something like that using the gmp.h library ..

am i missing something too obvious?

cheers

---

### Post by MadCow108 on 2010-03-22
[http://gmplib.org/manual/Integer-Random-Numbers.html#Integer-Random-Numbers](http://gmplib.org/manual/Integer-Random-Numbers.html#Integer-Random-Numbers)

---

### Post by MilEsSmiLes on 2010-03-22
thanks for that although i have seen that.. do you suggest to generate a random integer and then test if it is prime (and of course continue the loop if it isnt?) 

i am saying because this seems not efficient enough..

although i may be wrong, i will try it

---

### Post by MadCow108 on 2010-03-22
your looking for a primality test algorithm?
here are some examples (also note the references):
[http://en.wikipedia.org/wiki/Primality_test](http://en.wikipedia.org/wiki/Primality_test)

here's an implementation of miller rabin in gmp:
[http://en.literateprograms.org/Miller-Rabin_primality_test_(C,_GMP](http://en.literateprograms.org/Miller-Rabin_primality_test_(C,_GMP))

I do not know if something like that is preimplemented in gmp, you'll have to check yourself

but the C++ cln library has one if C++ is an option:
[http://www.ginac.de/CLN/cln_4.html#SEC36](http://www.ginac.de/CLN/cln_4.html#SEC36)
*isprobprime*

---

### Post by Lux Perpetua on 2010-03-22
> **MadCow108 said:**
> your looking for a primality test algorithm?I think our friend wants to *generate* prime numbers, which is not the same as testing a given number for primality. 

@MilEsSmiLes: I'm looking at [http://gmplib.org/manual/Number-Theoretic-Functions.html#Number-Theoretic-Functions](http://gmplib.org/manual/Number-Theoretic-Functions.html#Number-Theoretic-Functions), and I see ```
void mpz_nextprime (mpz_t rop, mpz_t op)
```Can't you just generate a random integer and take the next larger prime?

---

