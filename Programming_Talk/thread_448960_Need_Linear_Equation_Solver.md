---
title: "Need Linear Equation Solver"
date: 2007-05-19
forum: Programming Talk
---

### Post by josesanders on 2007-05-19
Does anyone know of an efficient linear equation solver that will solve a sparse linear system?  I need to be able to call it as a function from a C program.

I also need a good solver for large-scale mixed integer optimization problems if anyone knows of one.  Right now I use CPLEX, but I only have it for Windows, and I would very much like to use an open-source linux solver.

---

### Post by gborzi on 2007-05-19
Your question is a broad one. The answer depends on the size of the linear system and on its characteristics (real or complex, SPD or only symmetric, or unsymmetric, etc.). I suggest you to open synaptic and search for "sparse" in description and name. I found some libraries that use direct methods on sparse matrices, e.g. libsuperlu3.

---

### Post by Lux Perpetua on 2007-05-19
Take a look at Sherry Li's page: [http://crd.lbl.gov/~xiaoye/](http://crd.lbl.gov/~xiaoye/)

Here is a nice list of direct solvers: [http://crd.lbl.gov/~xiaoye/SuperLU/SparseDirectSurvey.pdf](http://crd.lbl.gov/~xiaoye/SuperLU/SparseDirectSurvey.pdf)

---

### Post by hod139 on 2007-05-20
For sparse systems, I recommend [CSparse.]("http://people.scs.fsu.edu/%7Eburkardt/c_src/csparse/csparse.html") (The more [up to date page]("http://www.cise.ufl.edu/research/sparse/CSparse/") seems to be down at the moment)

The only free MIP solvers that I know of are [lp_solve]("http://lpsolve.sourceforge.net/5.5/") and [glpk]("http://www.gnu.org/software/glpk/"). I doubt these solvers are as good as the commercially developed solvers, but they are free.  If you have access to matlab, the optimization toolbox is very good.

---

### Post by josesanders on 2007-05-21
Thank you for all of the responses.  I wasn't sure if anyone on this forum would know what I am talking about.

I think I am going to go with CSparse.  Forgive me, but I am new to linux programming so I was hoping you might be able to give me some tips on how to use the library.  I've downloaded the source code and when I run the make command, it creates a bunch of .o files corresponding to the .c files in a Lib directory.  There is a main header file in the Include directory.  What I did then was write a simple program to call a function cs_qrsol(...).  I include the main header file with the following line in the beginning of my code:

#include "./Include/cs.h"

Then I try to compile the program with the following:

$ g++ program.c -g Lib/*.o

It gives an error, "Undefined reference to cs_qrsol..."  I assume that means it can't link to the library.  Can someone point me to a simple explanation of how to link to these .o files?

---

### Post by hod139 on 2007-05-21
After you type make, a library is created: libcsparse.a
It is located in the lib subdirectory.  This is the library you want to link against.  In gcc (g++ is used for C++ not C), to link you use the -L flag to set the path to the library and the -l flag to set the name.  For your example, you would write:
```

 gcc -Wall -g program.c -oprogram -LpathToCSparseLib -lcsparse -lm

```

The -Wall flag turns on all warnings
The -g flag enables debugging symbols
The -o names the resulting binary program
-L tells the linker where to find the library
-l tells the linker to link against the libraries, in this case the csparse library and the math library

---

### Post by josesanders on 2007-05-21
Thanks a lot hod139!  Everything works now.

---

### Post by josesanders on 2007-05-23
Do you have CSparse working correctly?  I thought that I had it working because I compiled it and there are no errors, but whenever I try to solve a sparse linear system, the return value is zero and it doesn't overwrite the b vector with the solution.  When I use the print function to output the matrix, everything looks fine.  I'm just trying to test it with a 2x2 system.  Here is my code:

```
#include "./Include/cs.h"
#include <stdlib.h>

int main()
{

        cs A;
        cs At;
        A.nzmax=4;
        A.m=2;
        A.n=2;
        A.i=malloc(A.nzmax*sizeof(int));
        A.p=malloc((A.n+1)*sizeof(int));
        A.x=malloc(A.nzmax*sizeof(double));
        A.nz=-1;

        double* b=malloc(A.n*sizeof(double));

        b[0]=1;
        b[1]=2;


        // Column 1
        A.p[0]=0;

        A.i[0]=0;
        A.x[0]=1;

        A.i[1]=1;
        A.x[1]=3;

        A.p[1]=2;


        // Column 2
        A.i[2]=0;
        A.x[2]=2;

        A.i[3]=1;
        A.x[3]=4;

        A.p[2]=4;

        int val;

        cs_print(&A,1);
        val=cs_lusol(5,&A,b,0.001);
        printf("Returned %d\n",val);

        int i;


        for(i=0;i<2;i++) printf("X%d: %8.4f\n",i+1,b[i]);

        free(A.p);
        free(A.i);
        free(A.x);
        free(b);
        return 1;
}

```

And here is the output:
```
CSparse Version 2.2.0, May 31, 2007.  Copyright (c) Timothy A. Davis, 2006-2007
2-by-2, nzmax: 4 nnz: 4, 1-norm: 6
    col 0 : locations 0 to 1
      0 : 1
      1 : 3
    col 1 : locations 2 to 3
      0 : 2
      1 : 4
Returned 0
X1:   1.0000
X2:   2.0000

```

Do you have any ideas?  Thanks again for your help.

---

### Post by josesanders on 2007-05-23
Nevermind, I figured out what my problem was.  When I called the solver, I forgot to change the order when I switched from a 5x5 system to a 2x2 system.

---

