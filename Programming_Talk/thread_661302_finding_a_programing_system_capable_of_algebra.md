---
title: "finding a programing system capable of algebra"
date: 2008-01-07
forum: Programming Talk
---

### Post by evil107 on 2008-01-07
i've been learning basic programing lately on python and I thought it was about time I taught it some algebra like linear systems. unfortunatly I don't believe python is capable of doing so without feeding it the variables, does anyone know any ubuntu friendly programing systems capable of algebra or anyway to have python do it?

---

### Post by ghostdog74 on 2008-01-07
you should search the internet first. One such thing is[ sage]("http://en.wikipedia.org/wiki/Software_for_Algebra_and_Geometry_Experimentation"). There are others.

---

### Post by duff on 2008-01-07
SymPy -- [http://code.google.com/p/sympy/](http://code.google.com/p/sympy/)

---

### Post by amo-ej1 on 2008-01-08
wouldn't you be better of using GNU octave ([www.octave.org](www.octave.org)) which is an open source matlab clone. This will probably be more suitable for your needs.

---

### Post by popch on 2008-01-08
One of the programming languages routinely put to such use is Prolog (Programming in logic).

There's an implementation in the repos, called SWI Prolog. 'SWI Prolog' also is a good starting point for googling.

The standard introductory text would be 'programming in Prolog' by Clocksyn/Mellish (sp?)

---

### Post by chichilalescu on 2008-01-10
you can install a relatively friendly program, wxmaxima, that can do a lot of stuff, including linear algebra.

if you know c++, try to install the GiNaC library, though it's possibly too advanced for just linear algebra.

I don't use octave, because I need symbolic computations, but it should also work very well.

---

### Post by boban on 2008-01-10
I think you can do linear algebra with Python too... Check out [ NumPy and SciPy ]("http://www.scipy.org/more_about_SciPy") packages... I started learning python just recently so I don't have lot of experience with those, but they look very nice... Added bonus - they are in repos.

On the other hand, if  you know c/c++ or fortran, go and check out [blas]("http://www.netlib.org/blas/"). I think there are java wrappers available for it (and perhaps there are bindings for python - search for blas or lapack).

---

### Post by Sporkman on 2008-01-11
For symbolic processing, you can try [Mathematica]("http://www.wolfram.com/products/mathematica/index.html")...

---

### Post by evymetal on 2008-01-13
Try using pylab :
[http://www.scipy.org/PyLab](http://www.scipy.org/PyLab)

it's just like matlab but within python.

---

