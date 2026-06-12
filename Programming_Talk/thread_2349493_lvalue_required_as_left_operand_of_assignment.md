---
title: "lvalue required as left operand of assignment"
date: 2017-01-15
forum: Programming Talk
---

### Post by pyrex2 on 2017-01-15
Hello! I've been working with Software Defined Radios and while compiling some tools I ran into an error: lvalue required 

```
Scanning dependencies of target LTE_MISC
[  5%] Building CXX object src/CMakeFiles/LTE_MISC.dir/capbuf.cpp.o
In file included from /root/LTE-Cell-Scanner/src/capbuf.cpp:29:0:
/root/LTE-Cell-Scanner/include/dsp.h: In function ‘itpp::cvec fshift(const cvec&, double, double)’:
/root/LTE-Cell-Scanner/include/dsp.h:47:25: error: lvalue required as left operand of assignment
     coeff.real()=cos(k*t);
                         ^
/root/LTE-Cell-Scanner/include/dsp.h:48:25: error: lvalue required as left operand of assignment
     coeff.imag()=sin(k*t);
                         ^
/root/LTE-Cell-Scanner/include/dsp.h: In function ‘void fshift_inplace(itpp::cvec&, double, double)’:
/root/LTE-Cell-Scanner/include/dsp.h:64:25: error: lvalue required as left operand of assignment
     coeff.real()=cos(k*t);
                         ^
/root/LTE-Cell-Scanner/include/dsp.h:65:25: error: lvalue required as left operand of assignment
     coeff.imag()=sin(k*t);
                         ^
src/CMakeFiles/LTE_MISC.dir/build.make:62: recipe for target 'src/CMakeFiles/LTE_MISC.dir/capbuf.cpp.o' failed
make[2]: *** [src/CMakeFiles/LTE_MISC.dir/capbuf.cpp.o] Error 1
CMakeFiles/Makefile2:121: recipe for target 'src/CMakeFiles/LTE_MISC.dir/all' failed
make[1]: *** [src/CMakeFiles/LTE_MISC.dir/all] Error 2
Makefile:138: recipe for target 'all' failed
make: *** [all] Error 2


```


Does anyone know why this may be happening? And how I can fix it?

---

### Post by 3246251196 on 2017-01-16
coeff.real() returns a temporary value that is created on the stack and copied (rvalue). There is no memory address for it. It looks like real() just returns a copy of the coefficients value in real terms. It is not a way to set the value.

There must be another API? 

If real() returned a reference to the variable/member you are trying to change that would be okay, since a reference is an lvalue.

Is there no way to do something like coeff._real = cos(k*t) - for example. Or, coeff.setReal( cos(k*t) );

---

### Post by norobro on 2017-01-16
That error is due to a change in c++11.

Try adding "-std=c++03" to CXX_FLAGS in the CMakeLists.txt file in the application root directory.
It should look something like this: ```
SET (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++03 ...original options...")
```

---

### Post by pyrex2 on 2017-01-16
I'm not quite sure honestly... I have been tinkering to try and fix the issue and this got it to compile passed this part but I hit yet another one of these lvalue issues...

>     double e = cos(k*t);
    double f = sin(k*t);
    coeff.real(e);
    coeff.imag(f);

The source for the first part of the code I am having issues with is here: [https://github.com/Evrytania/LTE-Cell-Scanner/blob/master/include/dsp.h](https://github.com/Evrytania/LTE-Cell-Scanner/blob/master/include/dsp.h)

---

### Post by pyrex2 on 2017-01-16
Holy crap man... You rock! That fixed everything.....

> -std=c++03

Thank You!!!

---

### Post by mörgæs on 2017-01-16
Good, please mark the thread solved.

---

