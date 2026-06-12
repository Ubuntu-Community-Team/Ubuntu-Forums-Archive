---
title: "Lapack linking"
date: 2006-04-13
forum: Programming Talk
---

### Post by Huynam on 2006-04-13
Hi all,

I have used lapack in c++ on red hat previously and i had no problem to link the libraries with:

g++ test.C -L/usr/lib/ -llapack -lblas -lm -lg2c

Now I am working on my laptop which has Ubuntu with the lapack provided by Synaptic and the previous command didn't work anymore. It gave me:

/usr/bin/ld: cannot find -llapack
collect2: ld returned 1 exit status

So after a look to the usr/lib folder,  i changed the command by:
g++ test.C -L/usr/lib/liblapack.so.3 -lblas -lm -lg2c

But now I have another error:
/tmp/ccfwmBwU.o: In function `main':
test.c:(.text+0x151): undefined reference to `dgesv_'
collect2: ld returned 1 exit status

It seems that I don't export the function correctly. Does anyone have any idea about this?

Thanks 

Huy-Nam

ps: here is the code

#include <iostream>

#define MAX 10

extern "C" {
  extern void dgesv_(int *,int *,double *,int *,int*,double *,int*,int*); 
};
 
int main(){
   // Values needed for dgesv
   int n;
   int nrhs = 1;
   double a[MAX][MAX];
   double b[1][MAX];
   int lda = MAX;
   int ldb = MAX;
   int ipiv[MAX];
   int info;
   // Other values
   int i,j;

   // Read the values of the matrix
   std::cout << "Enter n \n";
   std::cin >> n;
   std::cout << "On each line type a row of the matrix A followed by one element of b:\n";
   for(i = 0; i < n; i++){
     std::cout << "row " << i << " ";
     for(j = 0; j < n; j++)std::cin >> a[j][i];
     std::cin >> b[0][i];
   }

   // Solve the linear system
   dgesv_(&n, &nrhs, &a[0][0], &lda, ipiv, &b[0][0], &ldb, &info);

   // Check for success
   if(info == 0)
   {
      // Write the answer
      std::cout << "The answer is\n";
      for(i = 0; i < n; i++)
        std::cout << "b[" << i << "]\t" << b[0][i] << "\n";
   }
   else
   {
      // Write an error message
      std::cerr << "dgesv returned error " << info << "\n";
   }
   return info;
}

---

### Post by jpkotta on 2006-04-22
Did you install the -dev package?  I don't think the .so works for linking, you need the .a.

---

### Post by Huynam on 2006-04-23
Hi,

I actually found the problem. I needed to install the package lapack3 and not the simple lapack....

Huy-Nam

---

### Post by Chris Johnson on 2006-12-14
I'm trying to get the sample code above to compile. I've installed lapack3, lapack3-dev, refblas3, refblas3-dev, atlas-base, atlas-base-dev and atlas-headers, and have tried the commands
```

g++ test.C -L/usr/lib/liblapack.so.3 -lblas -lm -lg2c
```
and```

g++ test.C -L/usr/lib/liblapack.a.3 -lblas -lm -lg2c
```

both of which generate the error:
```

/tmp/ccdBoSyI.o: In function `main':lapacktest.cpp:(.text+0x13d): undefined reference to `dgesv_'
collect2: ld returned 1 exit status
```

Can anyone help? I'm a complete newbie at how libraries etc. in G++ and linux work. If its relevant, I'm also running an AMD-64 build of Dapper Drake.

Cheers

---

### Post by Chris Johnson on 2006-12-14
Never mind - problem solved by using -llapack

---

