---
title: "[C++] Efficient symmetric sparse matrix storing"
date: 2013-10-25
forum: Programming Talk
---

### Post by erotavlas on 2013-10-25
Hi,

I have to implement in C/C++ a symmetric sparse matrix. I have read of various storage format and the most popular is this one CSR [http://netlib.org/linalg/html_templates/node91.html#SECTION00931100000000000000](http://netlib.org/linalg/html_templates/node91.html#SECTION00931100000000000000). This method is efficient from the memory requirement perspective, but it is no efficient in my case. In fact, I have three constraints: the first is that the dimensions and the matrix are not known in advance but the matrix is dynamically built, the second is that the elements of the matrix are updated during the computation and finally the matrix-vector and matrix-matrix operations must be efficient.
For the first and second constraint I think that something like this struct{double val; size_t i; size_t j;} vector<struct entry> myMatrix; is not efficient. In fact I have to search over a vector to find the right position for the elements and this require O(n) where n is the size of the vector.
I have thought about two possibilities: the first is to use a vector<map<int, double> > myMatrix; where the vector is row-wise and each map stores only non zero elements in the column. The first and second constraints are easily handled thank to the fast search over a map O(log ci) where ci are the number of non zero elements in the row ri. Also the matrix-vector and matrix-matrix multiplication is fast as in the case of vector<struct entry>. This representation is also more efficient in term of memory with respect to vector<struct entry>, but less with respect to CSR. The second is map<struct entry> myMatrix. This is similar to vector<struct entry> but allows faster searches.
I think that the best is vector<map<int, double> > but I worried about the following fact: in case of symmetric matrix is necessary to store only upper(lower)-triangular part of the matrix. So the first row is full and has n elements, the second row has n-1 elements and the last row has 1 element. In this case the last map has only one element. In the case of symmetric sparse matrix this is also more important.
I cannot use the solution of vector<vector<double> > since that the search is still O(n) even if moving down to the matrix the n decreases up to 1. Another important problem that is practical, instead of theoretical, is the cache coherence. A vector can be contiguously allocated, is it possible with a map? Of course I can use an unordered_map instead of map. The search become constant but the constant can be high. So the game is worth the candle?!
Do you have more clever idea? Any suggestion is welcome.

Thank you

---

### Post by ofnuts on 2013-10-26
If you are looking for something really efficient, I doubt that using vector/map is going to help, because these are very general-purpose objects and if I trust their global efficiency, I don't think they are going to be efficient enough for you (you may end up using a lot more memory than you think, for instance).

If you do a lot of updates, you will have to allocate memory, and this maybe another bottleneck. The default memory allocators (malloc()/new) can't take advantage of the specific behavior of your data.  

It would also help to know how big your matrices are going to be and how sparse they are...

---

### Post by zobayer1 on 2013-10-26
What does your matrix represent here? A graph like data structure? Also about the search, what are you really going to search here? The presence of a specific <int, double> key-value pair in a row or something else? And as [**[COLOR=#000000]ofnuts[/COLOR]**]("http://ubuntuforums.org/member.php?u=1382218") said, if you are worried about memory constraints, vector is not a good idea. Reading from your description, it doesn't look like there is any straight forward data structure that will be suitable for your scenario. Probably you will be needing to maintain some metadata structure along with actual data structure to support the dynamic resizing of your matrix and write some wrapper methods to support the symmetrical behavior of your matrix.

---

### Post by erotavlas on 2013-10-27
> **ofnuts said:**
> If you are looking for something really efficient, I doubt that using vector/map is going to help, because these are very general-purpose objects and if I trust their global efficiency, I don't think they are going to be efficient enough for you (you may end up using a lot more memory than you think, for instance).

If you do a lot of updates, you will have to allocate memory, and this maybe another bottleneck. The default memory allocators (malloc()/new) can't take advantage of the specific behavior of your data.  

It would also help to know how big your matrices are going to be and how sparse they are...

In general, I don't know how my matrices are sparse and big. I specify a quantity of memory at the beginning of the program and it allocates memory for matrices. In the case of square dense non symmetric matrix I have NxNxdouble while in symmetric case Nx(N+1)/2xdouble space. In the case of symmetric sparse square matrix I have hxNx(N+1)/2xdouble where h is sparse coefficient. In general I aspect to use N=10000-20000 in non sparse case and about the double in sparse case.
If I use a vector, I can allocate my memory in advance. I cannot do this with map. 
What do you suggest to use?

---

### Post by ofnuts on 2013-10-27
If you don't know how sparse your matrices are then I don't see much gain in handling them as sparse because when you hit a not-so-sparse matrix (which would be a 20% fill ratio) the whole thing will get much worse than using a plain matrix. 
 
If your problem is mostly dynamically reallocating the array, remember than in C an array is really a vector of pointer to the rows, so you can reallocate each row independently when you need to write past the end of the existing one (various strategies are possible for how much you reallocate each time). This can be done in an access method that  handles this dynamic reallocation as well as the symmetry.

---

### Post by MadCow108 on 2013-10-27
seems like you want the dok (dictionary of keys) or lil (row based linked list) format and then convert it to a more efficient one when you are done building it for processing.
there are plenty of libraries for this stuff, I know of the scipy.sparse module which implements coo, csc, csr, dia, dok and lil formats ([http://docs.scipy.org/doc/scipy/reference/sparse.html](http://docs.scipy.org/doc/scipy/reference/sparse.html))
I'm sure you can find a C++ library for these too, I think scipys implementation is partly based on arpack.

---

