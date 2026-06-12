---
title: "c++ matrix multiplication"
date: 2006-11-15
forum: Programming Talk
---

### Post by neoflight on 2006-11-15
Folks,

I was wondering whether there is any matrixstuff.h kinda file to deal with matrix multiplication and indexing.

so that i can simply do  something like...

#include <matrixstuff>
{
.
.
.

multiplyAB = A[m][n] * B[n][m];   ....???? 
.
}


I am dealing with huuuuge matrices (so pain to worry about matrix manipulations...)and running time is a factor.... iam new to c++ too...

Thanks for the help...

---

### Post by hod139 on 2006-11-15
There are no standard matrix/linear algebra/numerical packages in C++ (that's why there is matlab!!).  

If speed isn't too much of a concern and you just want to get something working, check out [SVL]("http://www.cs.cmu.edu/%7Eajw/doc/svl.html") (simple vector library).  If speed really is an issue, then I would suggest checking out 
[Boost::ublas]("http://www.boost.org/libs/numeric/ublas/doc/index.htm")
[ATLAS]("http://math-atlas.sourceforge.net/") (Automatically tuned linear algebra software)
[CBLAS]("http://www.intel.com/software/products/mkl/docs/mklqref/cblas.htm") (C binding to Fortran BLAS)

---

### Post by jstrube on 2006-11-17
Have you tried
[Eigen]("http://eigen.tuxfamily.org/") ?

I haven't used it myself, but it maybe worth giving it a shot.

---

### Post by hod139 on 2006-11-17
I had never heard of Eigen before, however this looks like quite the limitation:
> 
[Eigen]("http://eigen.tuxfamily.org/namespaceEigen.html") doesn't allow non-square matrices


---

### Post by junglepeanut on 2006-11-17
I would go with hod139 advice.


 Or you could write a Fortran piece that does what you want and then call it from C, just remember ( I think this is the case as I too am new to programming.) C and Fortran store matrices differently.

I work with matrices using Fortran because it is easy, C++ programmers I know  write their matrix stuff in Fortran.

---

### Post by amo-ej1 on 2006-11-20
the open matlab clone gnu octave is written in c/c++ and they also rely on standard libraries (afaik) so i doubt that there isn't any library capable of doing simple matrix manipulation. Is there really nothing in 
*apt-cache search matrix | grep lib* that can be of any assistance here ?

---

### Post by neoflight on 2006-11-20
> **amo-ej1 said:**
> the open matlab clone gnu octave is written in c/c++ and they also rely on standard libraries (afaik) so i doubt that there isn't any library capable of doing simple matrix manipulation. Is there really nothing in 
*apt-cache search matrix | grep lib* that can be of any assistance here ?

amazing....i got this as a part of the output....

> libnewmat10 - matrix manipulations C++ library
libnewmat10-dev - matrix manipulations C++ library


here is the stuff on newmat. looks good. 
[http://www.robertnz.net/nm10.htm#custom](http://www.robertnz.net/nm10.htm#custom) 
i tried to make the libs for it and i couldnt... actually i dont know how to do it properly...someone in my office helped and we got confused in the end and left it there...

BTW, how do i use the libnewmat10 et al in my c++ code....some help would be helpful as i am new to c++....thanks...

---

### Post by llonesmiz on 2006-11-20
If you install libnewmat10-dev you can see an example application (with comments) in:

/usr/share/doc/libnewmat10-dev/examples/example.cpp.gz

To compile it you need to extract the file example.cpp to a directory you own (the Desktop for instance) and then using the terminal in that directory execute:

 gcc -o example -I/usr/include/newmat example.cpp -lnewmat

where -I/usr... is with a capital i and -lnewmat is with a normal L.

You should also look into the reference at:

[http://www.robertnz.net/nm10.htm#refer](http://www.robertnz.net/nm10.htm#refer)

Good luck.

---

### Post by neoflight on 2006-11-20
thank you llonesmiz.

It works using the command line with all the tags you  specified.. I installed code::blocks today and was trying the same example problem and getting a bunch of errors such as 'newmat' could not be found. so i added the entire path in the #include. then comes another series of errors....

> Linking console executable: /home/example
/usr/bin/ld: /usr/include/newmat: No such file: File format not recognized
collect2: ld returned 1 exit status


in code::blocks....
/usr/include/newmat was provided at settings>compiler and debugger> linker .

anyclue? i know this is getting specific to solving a specific problem...but any help will be much appreciated...

---

### Post by llonesmiz on 2006-11-20
Well I haven't used code::blocks but the include directory shouldn't go in the linker options. You have to look for a section named "include directories" or maybe "cppflags".

Edit: ok this is what you need to do:

go to Settings, then Compiler and debugger, select the "linker" tab and under "link libraries" press add, then enter "newmat" (without quotes). After that select the "directories" tab and under the "compiler" tab press add and enter "/usr/include/newmat" (again without quotes). Then you just build and run normally.

Good luck.

---

### Post by neoflight on 2006-11-20
> **llonesmiz said:**
> Well I haven't used code::blocks but the include directory shouldn't go in the linker options. You have to look for a section named "include directories" or maybe "cppflags".

Edit: ok this is what you need to do:

go to Settings, then Compiler and debugger, select the "linker" tab and under "link libraries" press add, then enter "newmat" (without quotes). After that select the "directories" tab and under the "compiler" tab press add and enter "/usr/include/newmat" (again without quotes). Then you just build and run normally.

Good luck.


Awesome.... thanks a lot friend..  I was adding the entire path (/usr/include/newmat) instead of just 'newmat' under link libraries.. now i can build and run....thanks again...:-D 

for those who might be interested....for matrix multiplication and all there is a library in C++ that can be installed from edgy repos..... libnewmat10 et al.

---

### Post by hod139 on 2006-11-20
boost, refblas, lapack, gsl, and atlas are all also in the repositories, and can do matrix multiplication (among many other things).

---

### Post by neoflight on 2006-11-22
> **hod139 said:**
> boost, refblas, lapack, gsl, and atlas are all also in the repositories, and can do matrix multiplication (among many other things).

thanks a bunch. I would have asked earlier !... i spent a lot of time trying to get some info on matrix manipulation in C++... linking with fortran seems to be a good idea..some one in my dept also suggested that...

has anyone used wxsmith in code::blocks to create a GUI for C++. I Would like to have user inputs (via GUI--so that i can explain the user what values my code is expecting. Mostly dealing with numbers instead of chars) in different fields while running the code. optimization kind of thing with various objective functions. i want to write my own code for those... please let me know...thanks...

---

### Post by muxecoid on 2007-03-18
Do I get any real performance boost from using ACML on AMD X2 processors  over ATLAS-SSE2 or even pure BLAS?

---

### Post by Singular on 2007-03-19
OpenCV is based on Intel IPP, but I dont remember if there is a package for Linux or not.

If you are doing anything related to image processing, it is a good library to look at.

---

### Post by jegerjensen on 2007-09-24
Another option is the Blitz++ package, which claims to be very efficient.

---

### Post by hod139 on 2007-09-24
> **jegerjensen said:**
> Another option is the Blitz++ package, which claims to be very efficient.

It must be revival of the old threads day.  Anyway, the last message on the dev list is dated *2005-06-21.*  Is this library still being developed or maintained?

---

