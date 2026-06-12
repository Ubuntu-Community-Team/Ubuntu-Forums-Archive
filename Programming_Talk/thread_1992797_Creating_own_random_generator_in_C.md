---
title: "Creating own random generator in C"
date: 2012-05-31
forum: Programming Talk
---

### Post by prismctg on 2012-05-31
Can someone post some idea about user-defined random number generator in C. Example:input no:1,2,3,4,5,6,7,8,9 output:963214578

---

### Post by lukeiamyourfather on 2012-05-31
What you're referring to is psuedo random. There's a lot of articles out there with various methods. If you need random numbers that are secure it can get pretty complicated.

[http://lmgtfy.com/?q=C%2B%2B+random+number](http://lmgtfy.com/?q=C%2B%2B+random+number)

---

### Post by prismctg on 2012-05-31
yeah i just want some psuedo of random no genarator for C .. and of course without random()

---

### Post by steeldriver on 2012-06-01
> **prismctg said:**
> Can someone post some idea about user-defined random number generator in C. Example:input no:1,2,3,4,5,6,7,8,9 output:963214578

What you seem to be describing is a (pseudo)random **shuffle** of the input sequence - that's not the same as generating a random number (although that would be part of it)

For the random number generation itself, a good elementary reference imho is the 'Numerical Recipes in..." books, e.g.

[http://apps.nrbook.com/c/index.html](http://apps.nrbook.com/c/index.html) [go to page 274]

Good luck

---

### Post by 11jmb on 2012-06-01
pseudo-random sequences are easy to generate. Many wireless systems will use a device called a linear feedback shift register (LFSR) to generate pseudo-random binary sequences (PRBS) which are used for things like frequency-hopping and CDMA

This can also be implemented in software easily as a way to build a map like you described. You could use a maximal polynomial with a unique seed, and you could map number n with n shifts after the seed.

[http://en.wikipedia.org/wiki/Linear_feedback_shift_register#Some_polynomials_for_maximal_LFSRs](http://en.wikipedia.org/wiki/Linear_feedback_shift_register#Some_polynomials_for_maximal_LFSRs)

---

