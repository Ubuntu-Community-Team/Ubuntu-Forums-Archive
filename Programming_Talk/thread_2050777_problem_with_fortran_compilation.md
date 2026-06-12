---
title: "problem with fortran compilation"
date: 2012-08-31
forum: Programming Talk
---

### Post by mendezm82 on 2012-08-31
Hi, I'm new in fortran and I trying to compile this code,

```
C**************************************************************
C
C   MINIMAL BASIS STO-3G CALCULATION ON HEH+
C
C   THIS IS A LITTLE DUMMY MAIN PROGRAM WHICH CALLS HFCALC
C
C***************************************************************
         IMPLICIT DOUBLE PRECISION(A-H,O-Z)
         IOP=2
         N=3
         R=1.4632D0
         ZETA1=2.0925D0
         ZETA2=1.24D0
         ZA=2.0D0
         ZB=1.0D0
         CALL HFCALC(IOP,N,R,ZETA1,ZETA2,ZA,ZB)
         END
```
but the ifort compilator yields the error:```
/tmp/ifortGzYdor.o: In function `MAIN__':
hf.f:(.text+0xba): undefined reference to `hfcalc_'
```

any suggest?
thanks in advancement

---

### Post by ofnuts on 2012-08-31
> **mendezm82 said:**
> Hi, I'm new in fortran and I trying to compile this code,

C**************************************************************
C
C   MINIMAL BASIS STO-3G CALCULATION ON HEH+
C
C   THIS IS A LITTLE DUMMY MAIN PROGRAM WHICH CALLS HFCALC
C
C***************************************************************
         IMPLICIT DOUBLE PRECISION(A-H,O-Z)
         IOP=2
         N=3
         R=1.4632D0
         ZETA1=2.0925D0
         ZETA2=1.24D0
         ZA=2.0D0
         ZB=1.0D0
         CALL HFCALC(IOP,N,R,ZETA1,ZETA2,ZA,ZB)
         END
but the ifort compilator yields the error:/tmp/ifortGzYdor.o: In function `MAIN__':
hf.f:(.text+0xba): undefined reference to `hfcalc_'

any suggest?
thanks in advancement
Where do you expect the code for the HFCALC routine to come from? Did you wrote it? is it in some library?

[This book]("http://books.google.fr/books?id=6mV9gYzEkgIC&pg=PA417&lpg=PA417&dq=hfcalc+fortran&source=bl&ots=0-PH90IwyD&sig=OWYWA4h5T3UXTOdwcb0VFkxTxBc&hl=en#v=onepage&q=hfcalc%20fortran&f=false") has the source code for the routine.

---

