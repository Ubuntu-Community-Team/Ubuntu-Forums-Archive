---
title: "openmp segmentation fault with ifort"
date: 2009-09-18
forum: Programming Talk
---

### Post by cholericfun on 2009-09-18
hi

i'm just starting to play around with openmp in fortran,
i prefer to use ifort instead of gfortran since it seems to have better performance (simple test case i just did had a 10x difference...)

however i have a problem with the ifort install in that i cannot use excessively large arrays, i found a few hits on the web but nothing concrete, there was something about ```
export stacksize=1g

``` which did not do anything.

i appreciate the test problem i am trying to run is excessivly large, i figured it was the best way to start seeing cache problems et cet.

the problem is also more evident when using openmp, i guess i know why (private copy)

so has anyone any ideas how to fix this or whether it even can be fixed?

thanks

---

### Post by MadCow108 on 2009-09-18
I don't know much about fortran but you could check if your running out of stack by increasing it:
ulimit - s somebigsize

---

### Post by TheStatsMan on 2009-09-18
Well not really answering your question but you may find this interesting, regarding the speed difference between ifort and gfortran. It appears the problem can be partially resolved with compiler options.

[http://www.nabble.com/gfortran-vs-ifort-td23665694.html](http://www.nabble.com/gfortran-vs-ifort-td23665694.html)

---

### Post by cholericfun on 2009-09-19
thanks to the statsman,
found that page as well later, very interesting.

(did a little difference but not as much as needed in my simple case-vectorization probably didn't happen)

i'll try the other stacksize option,
thanks to both!

---

### Post by cholericfun on 2009-09-19
ok,
thanks to ulimit it worked
```
ulimit -s unlimited
```

before it was set at 
```
stack size              (kbytes, -s) 8192
```


in case anyone is interested, i just programed a simple vector product with very large arrays and openmp
here are the compiler options:
```
gfortran -ffree-form -fopenmp -O3 -ftree-vectorize  -o vecg vec.f
ifort -FR -O3 -openmp -o veci vec.f 
```

and here are the speeds: first is ifort

real	0m0.218s
user	0m0.216s
sys	0m0.064s

real	0m1.805s
user	0m3.488s
sys	0m0.044s

---

### Post by nspattak on 2009-12-17
intel compilers are said to be faster than gnu. In real life I suggest you always try both of them. It has happened to me that gfortran was faster than ifort.

I would also like to point out that ifort is more aggresive optimising than gcc/gfortran.

Finally, regarding your initial question, openmp segments are placed in the heap (PLEASE CORRECT ME IF I AM WRONG) that is why you might need to set " ulimit -s " . ifort has some options for this (eg -auto-save) . i have not checked gfortran on this.

---

### Post by nspattak on 2009-12-17
One last thing, can you try also using -mfpmath=sse and/or -march=native and/or -mtune=native with gfortran and see if things improve?

hope I helped

---

