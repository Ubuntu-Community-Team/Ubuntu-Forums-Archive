---
title: "Compiling gfortran with blas"
date: 2012-05-31
forum: Packaging and Compiling Programs
---

### Post by sdventura on 2012-05-31
Hi.

I recently upgraded to ubuntu 12.04. I am trying to compile the following simple code in fortran using the blas library.

```

      program test

      double precision a(5), b(5)
      integer i

      do i= 1,5
         a(i)= i
      enddo

      call dcopy(5, a, 1, b, 1) 

      do i= 1,5
         write(*,*) b(i)
      enddo

      end program

```I am trying to compile with the command line "gfortran -lblas test.f". However, I get the error message

```

/tmp/ccGxeiUD.o: In function `MAIN__':
problem.f:(.text+0x5e): undefined reference to `dcopy_'
collect2: ld returned 1 exit status

```I have both the packages libblas-dev and libblas3gf installed.
I just cannot understand what is going on.

I hope someone can help me.

Thank you in advance.

---

### Post by oldos2er on 2012-05-31
Moved to Packaging and Compiling Programs.

---

### Post by MadCow108 on 2012-06-01
try ```
gfortran test.f -lblas 
```
libraries should always go behind objects needing them

---

### Post by sdventura on 2012-06-01
Thanks.

---

