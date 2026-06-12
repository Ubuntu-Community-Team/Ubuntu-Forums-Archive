---
title: "Ubuntu 10.04 32 bit : Missing libpulse.a , libpulse-simple.a and libgssapi_krb5.a  ?"
date: 2011-06-25
forum: Packaging and Compiling Programs
---

### Post by gus193 on 2011-06-25
Hello, Im a newbie trying to compile from source. Now I have the following problem.

libpulse.a , libpulse-simple.a and libgssapi_krb5.a are missing in usr/lib after I installed libpulse-dev and libkrb5-dev. Does someone knows where to find libpulse.a , libpulse-simple.a and libgssapi_krb5.a for ubuntu 10.04 32 bit ?

I hope someone can help me.

---

### Post by gmargo on 2011-06-25
The **libpulse-dev** package provides the linkable shared library.  Why do you think you need static libraries?

---

### Post by gus193 on 2011-06-25
Hallo gmargo,

Because I want to make a statically linked binary from the source im compiling. That is why I need the static linkable libraries. 

I also have read somewhere that it is possible to make the static linkable libraries myself. But I dont know how to make a static linkable library from the pulseaudio source (ubuntu lucid lynx version) and MIT kerberos source (ubuntu lucid lynx version).

---

