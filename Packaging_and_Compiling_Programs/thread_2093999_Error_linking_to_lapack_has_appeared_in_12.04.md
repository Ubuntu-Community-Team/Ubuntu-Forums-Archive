---
title: "Error linking to lapack has appeared in 12.04"
date: 2012-12-12
forum: Packaging and Compiling Programs
---

### Post by unperson on 2012-12-12
I recently tried to re-compile a simple program I wrote previously using GMM++ (from the package libgmm++-dev) and Lapack, but after updating my operating system from lucid to precise, I am now getting an error during the linking process. There seems to be a problem linking to some of the functions provided by Lapack, but I can't understand the origin of the error and why it only occurs in the newer Ubuntu version. I hope this is the right place to ask for help on this.  

Below is a very simple test program using one of the offending functions.  When I attempt to compile it using g++ on my system , I get the error 
```
collect2: ld returned 1 exit status
```
It seems to be complaining about 
```
undefined reference to `zgeev_'
```
but as far as I can tell I have all the required libraries, so I can't quite understand what the problem is.

I ran nm and got
```

$ nm -D /usr/lib/liblapack.so | grep zgeev
00000000006e5270 T zgeev_
00000000006e7030 T zgeevx_

```
which as far as I can tell suggests the symbol zgeev_ is defined by the library.  I have confirmed that this program compiles just fine under lucid.  I have also installed the lapack-test package on my system and run the command 
```
xeigtstz < zgg.in
```
which says it "Tests of the Generalized Nonsymmetric Eigenvalue Problem routines" and reports all tests passed.  I believe this test should include the zgeev function (though I haven't yet found explicit confirmation of that).

I would file a bug report, except I can't tell if the problem is with g++, liblapack, libgfortran3, or maybe libgmm++.

Any insight on the root of the problem would be appreciated.

System information:

Ubuntu Linux 12.04.1 (precise)
g++ (4:4.6.3-1ubuntu5)
GMM++ package -- libgmm++-dev (4.1.1-5ubuntu1)
Lapack package -- liblapack3gf (3.3.1-1)
Blas package -- libblas3gf (1.2.20110419-2ubuntu1)
gFortran package -- libgfortran3 (4.6.3-1ubuntu5)

Build command and errors:
```

$ g++ -llapack -lblas -lgfortran bug.cc
/tmp/ccPq2tbF.o: In function `void gmm::geev_interface_right<std::vector<std::complex<double>, std::allocator<std::complex<double> > > >(gmm::dense_matrix<std::complex<double> > const&, std::vector<std::complex<double>, std::allocator<std::complex<double> > > const&, gmm::dense_matrix<std::complex<double> >&)':
bug.cc:(.text._ZN3gmm20geev_interface_rightISt6vectorISt7complexIdESaIS3_EEEEvRKNS_12dense_matrixIS3_EERKT_RS7_[void gmm::geev_interface_right<std::vector<std::complex<double>, std::allocator<std::complex<double> > > >(gmm::dense_matrix<std::complex<double> > const&, std::vector<std::complex<double>, std::allocator<std::complex<double> > > const&, gmm::dense_matrix<std::complex<double> >&)]+0x208): undefined reference to `zgeev_'
bug.cc:(.text._ZN3gmm20geev_interface_rightISt6vectorISt7complexIdESaIS3_EEEEvRKNS_12dense_matrixIS3_EERKT_RS7_[void gmm::geev_interface_right<std::vector<std::complex<double>, std::allocator<std::complex<double> > > >(gmm::dense_matrix<std::complex<double> > const&, std::vector<std::complex<double>, std::allocator<std::complex<double> > > const&, gmm::dense_matrix<std::complex<double> >&)]+0x35d): undefined reference to `zgeev_'
collect2: ld returned 1 exit status

```



Test code (bug.cc):
```

#include <complex>
#define GMM_USES_LAPACK
#include <gmm/gmm.h>

typedef std::complex<double> scalar;

int main()
{
    try {

        gmm::dense_matrix<scalar> A(4,4);
        gmm::dense_matrix<scalar> U(4,4);
        A(0,1) = 1; A(1,0) = -1; A(2,2)=3; A(3,3)=4;
        std::vector<scalar> Eig(4);
        gmm::geev_interface_right(A,Eig,U);

    }
    GMM_STANDARD_CATCH_ERROR;

    return 0;
}
```

---

### Post by MadCow108 on 2012-12-16
libraries need to be put behind objects needing their symbols since 11.04:
```
g++ bug.cc -llapack -lblas -lgfortran
```

this is due to the linker flag --as-needed

---

