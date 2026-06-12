---
title: "umfpack - undefined reference"
date: 2012-06-29
forum: Programming Talk
---

### Post by mes445 on 2012-06-29
Downloaded and compiled UMFPACK [1] and it went well
copied out the example program Tim Davis has written up and I got this error

me@sun:~/umfpack$ cc ex.c
/tmp/ccBVFK6B.o: In function `main':
ex.c:(.text+0x4a): undefined reference to `umfpack_di_symbolic'
ex.c:(.text+0x7b): undefined reference to `umfpack_di_numeric'
ex.c:(.text+0x87): undefined reference to `umfpack_di_free_symbolic'
ex.c:(.text+0xc6): undefined reference to `umfpack_di_solve'
ex.c:(.text+0xd2): undefined reference to `umfpack_di_free_numeric'
collect2: ld returned 1 exit status

I had originally thought that I would need to use libraries like such:

me@sun:~/umfpack$ cc ex.c -lumfpack -lamd -lcblas -latlas

but the libraries can't be found.

I had to adjust the paths for a few header files already, so this is probably the same issue , I just don't know where or what needs fixing. 

Any help is much appreciated.

[1] compile guide - [URL="http://matrixprogramming.com/2008/03/umfpack"]http://matrixprogramming.com/2008/03/umfpack
[/URL][2] user guide - [http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CFAQFjAA&url=http%3A%2F%2Fwww.cise.ufl.edu%2Fresearch%2Fsparse%2Fumfpack%2FUMFPACK%2FDoc%2FUserGuide.pdf&ei=Nr_tT8CwHIj56QG0wpicCg&usg=AFQjCNE_EdwSAR8jVH66llkkU0kOWk3YxA&sig2=uj7hpeJYhqiwjQ1vn3vbig](http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CFAQFjAA&url=http%3A%2F%2Fwww.cise.ufl.edu%2Fresearch%2Fsparse%2Fumfpack%2FUMFPACK%2FDoc%2FUserGuide.pdf&ei=Nr_tT8CwHIj56QG0wpicCg&usg=AFQjCNE_EdwSAR8jVH66llkkU0kOWk3YxA&sig2=uj7hpeJYhqiwjQ1vn3vbig)

---

### Post by mes445 on 2012-06-29
Fixed it using the Makefile from the Demos and turning off BLAS.
Not 100% sure yet how BLAS affects this yet though.

---

