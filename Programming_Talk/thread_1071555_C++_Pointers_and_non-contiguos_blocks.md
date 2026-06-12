---
title: "C++ Pointers and non-contiguos blocks"
date: 2009-02-16
forum: Programming Talk
---

### Post by beren.olvar on 2009-02-16
Hi there,

I am trying to do a program that need dynamical allocation of memory in C++.
In particular I need to have a 3D array which can change its size, so I do
```

double ***some;
some=new double**[Nx];
for(int i=0; i<Nx;i++){
   some[i]=new double*[Ny];
   for(int j=0; j<Ny;j++){
      some[i][j]=new double[Nz];
   }
}

```
where, of course Nx,Ny and Nz, are previously determined.
After that I need to pass that matrix to some function
```

void function(double ***some){
   ...
   some[i][j][k]=something;
   ...
}

```
to get back the results.

The problem is that it works for little matrices, but for larger N? i start getting problems and SIGSEGV. Probably becouse of the memory is not being allocated in a continuos way, so doing "some[i][j][k]" in "function" gives back a wrong place in memory.

Can that be the problem? If so, how can I solve it?
hope there is an easy way!!

thanks!

---

### Post by jimi_hendrix on 2009-02-16
this sounds like a job for VECTORS!

---

### Post by croto on 2009-02-16
Actually, in your implementation of a three dimensional matrix, it wouldn't be a problem if memory allocation of different parts of your matrix is non-contiguous: you are not defining a three-dimensional matrix but a 1-d vector of 1-d vectors of 1-d vectors. What's confusing is that the syntax to access individual elements is the same. For example:
```

int mat1 = new double[10][11];
int mat2 = new double*[10]; for (int i=0;i<10;i++) mat2[i] = new double[11];

```
Here, mat1 and mat2 represent a 10x11 matrix, but mat1 is a contiguous representation and mat2 isn't. Now let's see how you access the element (2,3) of each matrix:
```

mat1[2][3] = 10;
mat2[2][3] = 10;

```
Even though these two statements look the same, they're semantically different. The first one is semantically equivalent to:
```

((double*)mat1)[2*10+3] = 10;

```
That is, it is like a one dimensional array of 10*11 elements. The second is equivalent to
```

(mat2[2])[3] = 10;

```
which first dereferences mat2 (since it is a 1-d vector of pointers) which gives you a pointer. Then you dereference this new pointer to finally access the element you want.

The problem you're having may be related to having too large matrices, which may not fit in memory. The total size of your matrix is approximately equal to:
sizeofpointer*Nx + sizeofpointer * Nx*Ny + sizeofdouble *Nx*Ny*Nz

On a 64bit platform, sizeofpointer is 8bytes and on a 32bits platform is 4 bytes. Sizeofdouble is 8bytes. Check that the total size fits in your memory.

---

### Post by beren.olvar on 2009-02-16
Ups! you are totally right croto! thank you very much!
indeed the problem wasn't the arrays, but the rucursion: "function" reached the max recursion level. I am working now on linearize it :'(

I tryed to mark the thread as "SOLVED" and to "thank you", but I dont see how.
any clue?

cheers!

---

### Post by croto on 2009-02-16
I know that "thank you"s are disabled for now because they were too much of a load to the forum system. Happy to know I helped. Happy hacking!

---

### Post by Andrey2009 on 2009-02-19
Be accurate by operation with large scale arrays on 64-bitnjo to system. Int &#8211; bad type for indexes.

Article: [Forgotten problems of 64-bit programs development](http://www.viva64.com/art-1-2-16511733.html)

---

