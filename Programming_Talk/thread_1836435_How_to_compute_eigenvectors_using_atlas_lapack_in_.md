---
title: "How to compute eigenvectors using atlas/ lapack in c?"
date: 2011-08-31
forum: Programming Talk
---

### Post by zz3271 on 2011-08-31
I want to perform principle component analysis on a covariance matrix.  I found online that dsyevr should give me what I want but there doesn't seem to be an atlas wrapper for that.  I found the following on [http://itf.fys.kuleuven.be/~rob/computer/lapack_wrapper/index.html](http://itf.fys.kuleuven.be/~rob/computer/lapack_wrapper/index.html)
but when I run it with the compiler g++ file.c -o out -llapack_atlas
it gives me an error..... I think it was something like int->void  error etc
Is there some step I'm missing for the wrapper function to work?  (should I call the fortran function directly?)  Or is there another better function I could use to get the eigenvectors out?  Any help is appreciated!


```
int dsyevr (char JOBZ, char RANGE, char UPLO, int N,
        double *A, int LDA, double VL, double VU,
        int IL, int IU, double ABSTOL, int *M,
        double *W, double *Z, int LDZ, int *ISUPPZ,
        double *WORK, int LWORK, int *IWORK, int LIWORK) 
{
        extern  void  dsyevr_ (char *JOBZp, char *RANGEp, char *UPLOp, int *Np,
                 double *A, int *LDAp, double *VLp, double *VUp,
                 int *ILp, int *IUp, double *ABSTOLp, int *Mp,
                 double *W, double *Z, int *LDZp, int *ISUPPZ,
                 double *WORK, int *LWORKp, int *IWORK, int *LIWORKp,
                 int *INFOp);
        int  INFO;
        dsyevr_ (&JOBZ, &RANGE, &UPLO, &N, A, &LDA, &VL, &VU,
           &IL, &IU, &ABSTOL, M, W, Z, &LDZ, ISUPPZ,
           WORK, &LWORK, IWORK, &LIWORK, &INFO);

  return  INFO;
}
```

---

### Post by karlson on 2011-08-31
> **zz3271 said:**
> I want to perform principle component analysis on a covariance matrix.  I found online that dsyevr should give me what I want but there doesn't seem to be an atlas wrapper for that.  I found the following on [http://itf.fys.kuleuven.be/~rob/computer/lapack_wrapper/index.html](http://itf.fys.kuleuven.be/~rob/computer/lapack_wrapper/index.html)
but when I run it with the compiler g++ file.c -o out -llapack_atlas
it gives me an error..... I think it was something like int->void  error etc
Is there some step I'm missing for the wrapper function to work?  (should I call the fortran function directly?)  Or is there another better function I could use to get the eigenvectors out?  Any help is appreciated!


```
int dsyevr (char JOBZ, char RANGE, char UPLO, int N,
        double *A, int LDA, double VL, double VU,
        int IL, int IU, double ABSTOL, int *M,
        double *W, double *Z, int LDZ, int *ISUPPZ,
        double *WORK, int LWORK, int *IWORK, int LIWORK) 
{
        extern  void  dsyevr_ (char *JOBZp, char *RANGEp, char *UPLOp, int *Np,
                 double *A, int *LDAp, double *VLp, double *VUp,
                 int *ILp, int *IUp, double *ABSTOLp, int *Mp,
                 double *W, double *Z, int *LDZp, int *ISUPPZ,
                 double *WORK, int *LWORKp, int *IWORK, int *LIWORKp,
                 int *INFOp);
        int  INFO;
        dsyevr_ (&JOBZ, &RANGE, &UPLO, &N, A, &LDA, &VL, &VU,
           &IL, &IU, &ABSTOL, M, W, Z, &LDZ, ISUPPZ,
           WORK, &LWORK, IWORK, &LIWORK, &INFO);

  return  INFO;
}
```

I'd look at this first
[http://www.netlib.org/clapack/what/double/dsyev.c](http://www.netlib.org/clapack/what/double/dsyev.c)

But why not consider R?  If you really feel like doing this in C/C++ look at R source code.

---

