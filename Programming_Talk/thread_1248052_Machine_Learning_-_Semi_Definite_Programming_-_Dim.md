---
title: "Machine Learning - Semi Definite Programming - Dimentionality Reduction"
date: 2009-08-23
forum: Programming Talk
---

### Post by jduro on 2009-08-23
For those crazy machine learning programmers,

I am trying to use Semi Definite Programming for dimensionality reduction.

I could successfully implement the idea using Sedumi (Semi Definite Programming Toolbox for Matlab) !! The examples given were quite straight forward.
Unfortunately I need to integrate this with an algorithms written in C.

I already tried to run it (Sedumi) inside octave but until now it didn't work. 

The equivalent of Sedumi for C is called CSDP which is working but it requires me to represent the problem in a sparse matrix format (which is a pain). Until now I haven't been able to represent the problem in this format. I could run CSDP in octave as well, but again the sparse matrix format [IMG]http://themachinelearningforum.org/components/com_kunena/template/default_ex/images/english/emoticons/sad.png[/IMG].

So first question:
How to represent the constraint plus the input Gram Matrix in a sparse format that would allow me to run this in CSDP.

On octave-forge there is a function called linprog (that is meant for semi definite programming) but I could not crack it to solve this problem because there is an unknown vector (which is considered has a constraint) that has to be positive semi definite.

Other option could be to install matlab then sedumi and try to run matlab from inside c code.
Second question: (do you guys think this is possible?)

What I am trying to do basically is to follow this paper equation:
Unsupervised Learning of Image Manifolds by Semidefinite Programming.
[www.machinelearning.org/proceedings/icml2004/papers/85.pdf]("http://www.machinelearning.org/proceedings/icml2004/papers/85.pdf")
The equations are in section 3.3. Maximize: Tr(K) subject......

Any Ideas?

---

