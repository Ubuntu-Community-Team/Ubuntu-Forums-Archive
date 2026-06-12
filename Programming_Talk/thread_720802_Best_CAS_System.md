---
title: "Best CAS System"
date: 2008-03-10
forum: Programming Talk
---

### Post by melopsittacus on 2008-03-10
Hello all, I would like to use a CAS (Computer Algebra System). I have already examined the following programs: 

- Maxima [[http://maxima.sourceforge.net/]](http://maxima.sourceforge.net/]), 
- Axiom [[http://axiom.axiom-developer.org/]](http://axiom.axiom-developer.org/]), 
- Sage [[http://www.sagemath.org/]](http://www.sagemath.org/]), 
- Yacas [[http://yacas.sourceforge.net/homepage.html]](http://yacas.sourceforge.net/homepage.html]). 

After browsing through the tutorial and introduction sections of these programs, and trying out some sample code, I found that they have more or less the same features, so now I cannot decide which one to use, and it would take too much time to learn all of them.

Are there any known advantages/disadvantages of these programs? Or is there a more detailed comparison of them than this one: [http://en.wikipedia.org/wiki/Comparison_of_computer_algebra_systems?](http://en.wikipedia.org/wiki/Comparison_of_computer_algebra_systems?)

For instance: is any of them faster than the others? (I did not experience any differences in speed for the basic operations)
Or is there one that is most widely used?

The only small problem I found so far is with Sage: it is not available as Ubuntu package, otherwise all four systems seem to be excellent, so I really don't know which one I should use...

---

### Post by Fbot1 on 2008-03-10
There's GiNaC but it kinda sucks.

---

### Post by WW on 2008-03-10
> **Fbot1 said:**
> There's GiNaC but it kinda sucks.
GiNaC is a C++ library for symbolic algebra.
From the GiNaC web page:
> 
The name GiNaC is an iterated and recursive abbreviation for GiNaC is Not a CAS, where CAS stands for Computer Algebra System. 

The poster asked for a CAS, so GiNaC is probably not what he or she wants.

---

### Post by Fbot1 on 2008-03-10
> **WW said:**
> GiNaC is a C++ library for symbolic algebra.
From the GiNaC web page:

The poster asked for a CAS, so GiNaC is probably not what he or she wants.

I'd consider it a CAS.

---

### Post by melopsittacus on 2008-03-11
Thanks for replying.

Is there anybody who has any experience with any of the four programs I mentioned above?

---

### Post by gernot.eger on 2008-05-29
Hi,
I don't have much personal experience, but found this while trying to solve the same:

[http://people.math.aau.dk/~slb/kurser/software/RCompAlg.pdf](http://people.math.aau.dk/~slb/kurser/software/RCompAlg.pdf)

Gives some insight on Axiom,Maxima and Yacas, published 2005
hope that helps,
Gernot

---

### Post by goldencako on 2008-05-30
I've been lookin into Axiom and if, by any chance, you want a powerful tool for symbolic integration, then your best best is Axiom. 

[http://en.wikipedia.org/wiki/Risch_algorithm#Implementation](http://en.wikipedia.org/wiki/Risch_algorithm#Implementation)

---

