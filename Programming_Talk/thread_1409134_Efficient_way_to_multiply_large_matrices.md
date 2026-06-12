---
title: "Efficient way to multiply large matrices"
date: 2010-02-17
forum: Programming Talk
---

### Post by banana_head on 2010-02-17
I am working with some large (over 1 million x 1 million), sparse matrices.  I need to multiply 7 of them together, and I am currently using Pythons scipy.sparse modules with the lil_matrix sparse class (before multiplication, I need to slice them, etc). When doing the multiplications, I can get 6 of them to multiply (it appears in any order), yet the 7th fails with the following error message: 

[PHP]File "/usr/local/packages/scipy/0.7.1/lib/python2.4/site-packages/scipy/spars\
e/base.py", line 288, in __mul__
    return self._mul_sparse_matrix(other)
  File "/usr/local/packages/scipy/0.7.1/lib/python2.4/site-packages/scipy/spars\
e/base.py", line 341, in _mul_sparse_matrix
    return self.tocsr()._mul_sparse_matrix(other)
  File "/usr/local/packages/scipy/0.7.1/lib/python2.4/site-packages/scipy/spars\
e/compressed.py", line 299, in _mul_sparse_matrix
    indices = np.empty(nnz, dtype=np.intc)
ValueError: negative dimensions are not allowed[/PHP]

My code runs on a cluster and I tried to give this process a large amount of RAM, yet the last multiplication fails each time. Can anyone suggest what I should try to do to get this last matrix multiplied? My current plan is as follows: after building the matrices, write the 7th to disc, multiply the other 6, write those to disc. Then in a separate job, multiply those two together. I would however like to have this all accomplished in one process though, building the matrices already takes a few hours depending on which matrix class I use (so far it seems that lil is the fastest and memory efficient), and I need to do this process about 100 times while changing the values of the matrices.

Thanks!

---

### Post by avidday on 2010-02-17
How sparse are these matrices? Overall, sparse numpy is pretty efficient and I haven't seen that sort of behaviour working with similar sized single and double precision banded matrices from finite difference and finite element method discretization (so maybe 20-100 million non zeros in a 1e6x1e6 matrix). 

The back trace you are seeing suggests an internal failure pretty deep inside the library itself. You might be running out of memory, but that should be easy to check.

---

### Post by banana_head on 2010-02-17
The dimensions are 1,594,323 x 1,594,323, and there are exactly 4,782,969 non-zero entries (per matrix). Each matrix has non-zeros at the same (i,j) location, and I know these (i,j)'s (which makes building them much faster than exhaustively going through all entries). These matrices are non-symmetric, but have real entries. @Avidday, could you suggest a good memory monitoring scheme/program?

---

### Post by avidday on 2010-02-17
OK, so you are looking at something like 25Mb per instance of each matrix. Worst case, your application might need 1Gb of free ram. That doesn't sound excessive to me. 

The simplest way to get some memory statistics it is run your code (or sections of it) interactively inside a shell (I like ipython), and use standard Linux tools like top to see how the ipython image grows in size as your code runs.

There is a pretty good lower level memory profiler called [URL="http://guppy-pe.sourceforge.net/#Heapy"]heapy
[/URL] which you could try if you need more detail on what is going on.

---

### Post by banana_head on 2010-02-17
Thanks for the quick reply. Indeed, the matrices should not take up large amounts of ram, though while using top to monitor my processes, I noticed that calling the sparse matrix with the intended size allocates a large amount of ram on its own-right. It would be nice if I could tell the matrix a guess on the # of non-zeros, but I dont believe it allows for that. I will have a look at heapy, seems more up my alley. Using top has been my current method.

---

### Post by TheStatsMan on 2010-02-17
I have found scipy sparse module to be really slow. Pysparse seems to be a lot better.   The other option is given how trivial f2py makes it too link to fortran you could always just do the calculations in there. This is the approach I usually take. Yousef Saads Sparskit is written in Fortran and it can multiply matricies for most of the well known storage methods I think. The source is freely available at least for non-commercial useage. There are numerous other free and commercial libraries as well that would be suitable.

---

### Post by banana_head on 2010-02-17
Thanks for the reply. I have used PySparse and it works pretty well. The cluster I am running on does not have it installed yet, so I am not sure whether PySparse will multiply my matrices error-free. I have tested it on my mac, and it seems fast and more memory efficient. The main issue I have with PySparse is that the eigenvalue routine is for symmetric matrices. I am using the Lanczos routine for the non-symmetric real matrix that is the result of the multiplications, which is located in scipy.sparse. I could write my own algorithm for the type of arrays within PySparse to get the eigenvalues, but I would like to get around having to do a lot of hard coding for the time being.  

I will take a closer look at using f2py, I dont know much fortran though!

---

### Post by TheStatsMan on 2010-02-17
> **banana_head said:**
> Thanks for the reply. I have used PySparse and it works pretty well. The cluster I am running on does not have it installed yet, so I am not sure whether PySparse will multiply my matrices error-free. I have tested it on my mac, and it seems fast and more memory efficient. The main issue I have with PySparse is that the eigenvalue routine is for symmetric matrices. I am using the Lanczos routine for the non-symmetric real matrix that is the result of the multiplications, which is located in scipy.sparse. I could write my own algorithm for the type of arrays within PySparse to get the eigenvalues, but I would like to get around having to do a lot of hard coding for the time being.  

I will take a closer look at using f2py, I dont know much fortran though!

Fortran is so easy that I doubt you would have much trouble to learn it quickly. With f2py you can simply write the fortran subroutine compile it with f2py and then use it in Python. There are a few tricks to make it work better. There is a lot of fortran source code available for linear algebra so it may be less painful than you expect.

---

### Post by dankdave on 2012-05-01
Your resultant matrix could be getting filled in as you multiply your matrices.  Have you tried constructing them, one at a time as necessary?  That should help considerably if it's fairly cheap to construct them.

---

