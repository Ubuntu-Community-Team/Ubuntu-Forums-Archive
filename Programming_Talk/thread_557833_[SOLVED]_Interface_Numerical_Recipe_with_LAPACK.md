---
title: "[SOLVED] Interface Numerical Recipe with LAPACK"
date: 2007-09-23
forum: Programming Talk
---

### Post by neo.patrix on 2007-09-23
Hello all,

I have a **numerical computing** problem. 

I need to call a Fortran function **"zggev"** to get eigen values from C++. I have got interface headers clapack.h & f2c.h. My problem is converting my
Numerical Recipes typedef matrix of complex numbers namely *Mat_IO_CPLX_DP* into *doublecomplex* array for passing as argument to LAPACK function.

That is converting a 2-dimensional matrix to 1-dimensional array for usage with Fortran.

thank you.

---

### Post by hod139 on 2007-09-23
I'm not 100% sure what you are looking for.  Are you asking how to convert a dense C style 2 dimensional matrix into the sparse FORTRAN column-major representation?  What is a numerical recipes matrix (are you using the FORTRAN, C, or C++ implementation of numerical recipes?)


Below is some code that takes a boost matrix (B) and converts it to the FORTRAN sparse column major representation.  It's not going to be exactly what you want, but hopefully gives you the general idea.

```


int numNonZero = 0;
for (unsigned int i = 0; i < B.size1(); i++)
{
    for (unsigned int j = 0; j < B.size2(); j++)
    {
        if (B(i, j) != 0.0)
         {
            numNonZero++;
         }
    }
}

// FORTRAN representation uses 3 arrays, a value array containing the data, and two indexing arrays to access the data
int* rowArray = new int[numNonZero];
int* colArray = new int[numNonZero];
double* valArray = new double[numNonZero];

 numNonZero = 0;
for (unsigned int i = 0; i < B.size1(); i++)
{
    for (unsigned int j = 0; j < B.size2(); j++)
    {
        if (B(i, j) != 0.0)
        {  // use fortran indices, starting at 1
            rowArray[numNonZero] = i + 1;
            colArray[numNonZero] = j + 1;
            valArray[numNonZero] = B(i, j);
            numNonZero++;
        }
     }
}

// Call FORTRAN function

// Cleanup
delete[] rowArray;
delete[] colArray;
delete[] valArray;

```

---

### Post by neo.patrix on 2007-09-23
Hi 

thanks for code, i will try it out , if applicable

> 
Are you asking how to convert a dense C style 2 dimensional matrix into the sparse FORTRAN column-major representation?


Yes, exactly.

> 
What is a numerical recipes matrix (are you using the FORTRAN, C, or C++ implementation of numerical recipes?)


*Numerical Recipes in c++* is the book for algorithms dealing with all kinds
of numerical computation. The book suggests me to use Standard Fortran packages for finding Eigen values of a Complex Matrix.

NR provides a template matrix NRMat to deal will different numeric types.
I have got a concreate class from the template for dealing with complex numbers of double precision. Something like NRMat<complex<double>>. I need
to convert this into some column major array of type doublecomplex*

Now, doublecomplex is the structure provided to deal with complex numbers
in calling Fortran functions starting with "z". 

But , if we forget about complex numbers. It is simply conversion of 2D Matrix
in C++ to 1D doublecomplex array in C++. This array is used by function call
to Fortran library.

thanks again.

---

### Post by hod139 on 2007-09-24
> **neo.patrix said:**
> Hi 

thanks for code, i will try it out , if applicable/

I hope it is what you were looking for.

> 
*Numerical Recipes in c++* is the book for algorithms dealing with all kinds
of numerical computation. <snip> 

I am aware of the book, I was just wondering what edition you were using.  There is a numerical recipes in C edition and a numerical recipes in FORTRAN edition.

---

### Post by neo.patrix on 2007-09-25
Numerical Recipes in C++ 2.0,

Ok, I seemed easy , but unfortunately clapack.h, does not have exactly the function that i want to use "zgesvd_" ](*,)](*,)

also, I created my own function declaration using original fortran function definition
from LAPACK package for ZGESVD. The code was complied & linked successfully with the clapack.lib. So I believe that i have got correct function declaration now. :-k

But, no still the ouput is incorrect, SVD is creating very problem which is supposed to solve, It is giving me badly conditioned S, U, & V. 

I compared the result with MATLAB svd which also uses same zgesvd, but my
output is no where near to MATLAB output.:cry::cry:

I think there is some incorrect type conversion between my program & library.

---

### Post by neo.patrix on 2007-09-25
The problem of using ** zgesvd_** with Numerical recipes in C++
on MS VC++ 6.0 platform requires 

1) clapack.h
2) f2c.h

(Above mentioned files are not directly used , but are used nevertheless to create required header)

3) clapack.lib needs to be linked with your programs object code.

Since this functions deal directly with Numerical Recipes matrix library
follwoing you require

5) nrtypes.h         
6) nrutils.h

I have created header file for fuction zgesvd_ and also function that uses it, since it is not present in clapack.h, but use it with care, it may be working only for my particular scenario.

Lookout for attachments. questions are welcome.

---

