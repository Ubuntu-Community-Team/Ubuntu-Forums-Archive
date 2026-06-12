---
title: "Matrix Inversion on CUDA"
date: 2009-07-19
forum: Programming Talk
---

### Post by kjohansen on 2009-07-19
I need to find the inverso of a dense symmetric semipositive definite matrix on the GPU using CUDA.

There is a lot of literature out there from suggesting cholseky or LU decompositions to Lanzcos and Arnoldi iterations...

Does anyone have an opinion or recommendation on which algorithms fit CUDA best.

Right now I am thinking doing an LU decomp and then solving a system of equations for each column in an identity matrix might...

---

### Post by MadCow108 on 2009-07-19
what are you trying to solve?
usally you should avoid matrix inversion like the plaque because its slow and inaccurate.

You can solve almost everything without actually inverting matrices.

---

### Post by kjohansen on 2009-07-20
I am doing a low rank decomposition of a kernel matrix.

The decomposition becomes k_hat=k_lm*(k_mm)^-1*k_ml.

The idea is that k is too large to fit into the GPU memory, thus I can store three much smaller matrices and get a relative accuracy by replacing all matrix vector multiplication (say k*x where k is the matrix and x is a vector) with (k_lm*((k_mm)^-1*(k_ml*x))).


The k_mm matrix should be reasonably small.  Any useable decomposition will require the inverse of a matrix, so I have no choice but to invert...

---

### Post by TheStatsMan on 2009-07-21
Lancos and Arnoldi are iterative methods. They are used in solving large sparse systems, not dense ones. Since the matrix is symmetric you can use the cholesky it will be faster than the LU.

Note to solve A^(-1)*B, you would not inverse A. You should avoid direct inversion if possibile

---

### Post by Paul Miller on 2009-07-21
[This paper]("http://www.eecs.berkeley.edu/Pubs/TechRpts/2008/EECS-2008-49.pdf")'s author claims to have achieved ~300 Gflops using parallel LU on a GPU.

---

