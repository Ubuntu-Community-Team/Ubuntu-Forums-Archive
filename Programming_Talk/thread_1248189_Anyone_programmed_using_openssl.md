---
title: "Anyone programmed using openssl?"
date: 2009-08-23
forum: Programming Talk
---

### Post by mcweaver1 on 2009-08-23
I'm creating a program which uses a few openssl functions to encrypt data.  I've come across a VERY ANNOYING bug in my code and I was wondering if anyone could spot it.

The functions I am using are EVP_rc2_cbc(), EVP_CipherUpdate(), and EVP_CipherFinal_ex().  I am encrypting data using the rc2 block cipher in cipher block chaining mode.

I would post the code now but tbh I dont really want to go to all the effort of simplifying it (it is a pretty big program) and explaining the structures I am using if nobody is actually familiar with these openssl functions.

It is all in C btw.

---

