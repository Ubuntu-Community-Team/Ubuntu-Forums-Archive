---
title: "Sparse Matrix Libraries for C++"
date: 2012-05-01
forum: Programming Talk
---

### Post by dankdave on 2012-05-01
Hey All,

I have some existing C++ code and I need to solve a large, sparse, linear system many times.  My plan is to perform a single LU decomposition at the start of the run, and then simply use forward/backward substitutions for each of the future solves.

Can anyone recommend their favorite C / C++ sparse matrix library that would link easily into my existing code?

I've looked into a few libraries, but I find their lack of documentation concerning:

sparselib++: [http://math.nist.gov/sparselib++/](http://math.nist.gov/sparselib++/)
SuperLU: [http://crd-legacy.lbl.gov/~xiaoye/SuperLU/](http://crd-legacy.lbl.gov/~xiaoye/SuperLU/)

I'm not interested in digging deep into the guts of anyone elses code.  My requirements are the following:

1.) Will allow me to link to my existing C++ code.

2.) simple interface (ps - did I ever tell you how much I now appreciate Matlab?)

Thanks in advance.

---

### Post by dankdave on 2012-05-08
Jack Dongarra of the University of Tennessee has put together an excellent list of "Freely Available Software for Linear Algebra".  As of this posting, this list was last updated in September of 2011.

[http://www.netlib.org/utk/people/JackDongarra/la-sw.html](http://www.netlib.org/utk/people/JackDongarra/la-sw.html)

My question still stands, does anyone have experience with any of these libraries/packages, and if so, can you recommend any of them?

---

