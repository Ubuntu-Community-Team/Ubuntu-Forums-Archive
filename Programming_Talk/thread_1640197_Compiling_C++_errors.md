---
title: "Compiling C++ errors"
date: 2010-12-07
forum: Programming Talk
---

### Post by newport_j on 2010-12-07
[COLOR=black][FONT=Courier][SIZE=3]In file included from WEGtest.c:24:[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Courier][SIZE=3]WEGFunDefs.h:40: error: expected or before token[/SIZE][/FONT][/COLOR]
 
 
The above error I receive several times when I try to compile a program originally in c that compiles perfectly with gcc, but does not compile with g++. The file WEGFunDef.h line 40 is now shown. It is the second line.
 
 
```

[FONT=Times New Roman][SIZE=3]void CHN_RFL2( double *Gzv, int NZo, double *Zo, double *P2o,[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]                double FRQ, int NRFLc, double complex *RFLc);[/FONT][/SIZE]

```
 
 
Any help appreciated. Thanx in advance.
 
Newport_j

---

### Post by GeneralZod on 2010-12-07
At a guess (the best I can do given the minimal code snippet here), I'd say it was the usage of "double complex", which seems to be a C99 feature ([http://www.delorie.com/gnu/docs/glibc/libc_420.html](http://www.delorie.com/gnu/docs/glibc/libc_420.html)) that is not (to my knowledge) supported in C++.

See e.g.

[http://stackoverflow.com/questions/3332726/complex-number-types-in-mixing-c99-and-c](http://stackoverflow.com/questions/3332726/complex-number-types-in-mixing-c99-and-c)

---

### Post by talonmies on 2010-12-07
double complex is not valid in C++ (nor C90). In C++, the complex type is implemented as a template class which can be instantiated as either float, double or long double.

---

### Post by newport_j on 2010-12-08
I see what you mean. Double complex is available in c and not c++; some code rewriting is called for.
 
I think the best idea is to drop the whole complex.h, double complex thing. I would make a struct definition like 
 
struct complexx {
double real;
double imag;
};
 
and define new variables (to replace the ones type by double complex) from it and so forth. 
 
I want this code the be portable over c and c++. It seems that this would work. I would use the double complex type if it were only to compile in c, but it must also compile in c++.
 
If there is an easier way to accompish this please let me know.
 
Remember, I want to achieve portability over c and c++. I think this will do it, but it is a bit messy. If there is cleaner way to do it, please let me know.
 
 
Thanx in advance.
 
Newport_j

---

### Post by talonmies on 2010-12-08
> **newport_j said:**
> I
I think the best idea is to drop the whole complex.h, double complex thing. I would make a struct definition like 
 
struct complexx {
double real;
double imag;
};
 

Don't do that, it will beak lots and lots and lots of other parts of the code. It is time to familiarize yourself with the C preprocessor. There is a standard pre-processor symbol which all c++ compilers are required to define:

```
__cplusplus
```

You can check whether that is defined and then do something like this:

```

#ifdef __cplusplus
    typedef complex<double> dcomplex;
#else
    typedef double complex dcomplex;
#endif
```

which will define a type which is still compatible with the respective C and C++ standard library functions and only require some modest code changes to have code that will compile in either language.

---

### Post by newport_j on 2010-12-09
I can see where that would work. But you would have to place the statement 
 
#ifdef _cplusplus
typedef complex<double. dcomplex;
#else
typedef double complex dcomplex;
#endif
 
 
At the top of every function where double complex is now used in the c source. Also, you would need to put <complex.h> and <complex> at the top of every function where double complex is now used. You could not just use one 
, but both definitions (c and c++) of complex. Finally, every time a variable is defined as double complex they would need to be changed to dcomplex.
 
None of this is hard to do, please do not misundertsand I believe that it will work. 
 
It seems from what I have read on the internet that double complex is new as of c99. It was put there to help transitioning to c, FORTRAN programmers (yes, really). In my usage I just pretended that there never was a double complex added and created a structure that is compilable in both c and c++. I will stay away from reserved words like complex and define my own complexx. Again, like your example I will need to change some double complex definitions to complexx, yours requires changing double complex to dcomplex.
 
I think your is more sophisticated, certainly. But, mine is just keeping with the keep it simple stupid philosophy.
 
 
Please respond. I am interested in what you have to say.
 
 
Newport_j 
 
 
 
 
Also, I would need to

---

### Post by talonmies on 2010-12-10
> **newport_j said:**
> I can see where that would work. But you would have to place the statement 
 
#ifdef _cplusplus
typedef complex<double. dcomplex;
#else
typedef double complex dcomplex;
#endif
 
 
At the top of every function where double complex is now used in the c source. 
No.  You only need put that into a header which is included by each source  file. There might already be one that is included by every source file  in the project. add it to that.
> 
Also, you would need to  put <complex.h> and <complex> at the top of every function  where double complex is now used. You could not just use one 
, but both definitions (c and c++) of complex. 
Again no. How about this:

```

#ifdef _cplusplus
#include <complex>
typedef complex<double. dcomplex;
#else
#include <complex.h>
typedef double complex dcomplex;
#endif
```
 
> Finally, every time a variable is defined as double complex they would need to be changed to dcomplex.

Right,  and you have to do the same thing with your type, so there is no  difference in the number of changes required in the code. Except that  your new type is not compatible with any standard library functions  which take complex arguements and you will also have to re-write them. 

Incidentally, the approach I have suggest is also the method recommended in [http://www.drdobbs.com/184401628](http://www.drdobbs.com/184401628).

 
> Please respond. I am interested in what you have to say.
Make a pleasant change, I guess....

---

### Post by newport_j on 2011-01-03
Ok. let us go with that. I have a main *.c file that has no double complex in it. It does call a header file that does have a double complex in it. So where do I put the 
 
header sel_lang.h file that represents :
 
#ifdef _cplusplus
#include <complex>
typedef complexdouble complex, dcomplex;
#else
#include <complex.h>
typedef double comlex dcomplex;
#endif
 
I would say it goes in the original *.c that calls the header file. But, then I have looked at the source of both files and only the *.c file calls header files.
 
Anyway, where do I put the 
 
include "sel_lang.h"
 
In the header file section of the calling *.c file or the header file where the definition is actually used?
 
Thanx in advance for any help.
 
In my case sometimes the complex term (double complex) is used in the *.c file and sometimes in the *.h file.
 
I would say it is obvious when double complex is used in a *.c file; just put the sel_lang.h in the header file section for that *.c file. 
 
The case above is not so clear cut. The *.c file calls a header file and then the double complex is used. Thus my question.
 
Sorry for this round about question, but header files and c files are clear, it is the nesting that is not clear.
 
Newport_j

---

### Post by MadCow108 on 2011-01-03
I kind of doubt this whole approach of typedef'ing double complex will be successful.
The C and C++ complex type are not interchangable.
The C type is most probably implementation dependent and has regular functions as api, whereas the C++ type is a class with overloaded operators.
To the very least you'd have to write interface functions to map the C api to the C++ api.

Your probably better of either rewriting everything or compile the C code with a C99 compiler and just link it with your C++ code.

The latter approach is probably the easiest and least error prone approach.

---

### Post by worksofcraft on 2011-01-03
I recommend you choose either C or C++. Trying to embrace both languages as they continue to diverge is a lose-lose strategy IMO.

---

### Post by newport_j on 2011-01-04
We have it working in the c version. But the c version of the parallel software analyzer is being phased out. There is no future there, it is all in c++. I agree that being exclusively in c or c++ (not both) is the best approach. 
 
We are far more interested in the output. Getting the program to compile and run and then checking the output for correctness is the crucial, but that is only half the batlle. I think most people here (this Forum) are more into programaing than actually caring about the output. Our primary goal is analysis. The output of this program under different inputs is the holy grail. 
 
The analysis of each version is more complete in c++. I know that they (c and c++) are similar, but they are diverging. The main problem is now is dealing with the double complex concept in c, but in c++ things are different. There is no double complex in c++ so one must think up a compromise. I am new to preprocessor commandsa, but I think this will work.
 
First, determine which compiler is compiling (c or c++) and then based on that selection create a new variable dcomplex which fits for that compiler. 
 
The idea of completely rewriting this program in c++ is too horrible to contemplate.
 
I think that this will work. I appreciate your help.
 
Newport_j

---

### Post by MadCow108 on 2011-01-04
I guess you only want to link in the C code with the C++ code?
all else makes no sense.

In this case you'll also have to add a layer on top of the C API to convert the C++ complex type to a C type.
```

file: cpp_api.h
// C++ sees this. e.g. _realfunction(cpp_complex.real, cpp_complex.imag);
extern "C" _realfunction(float real, float imag);


file: real_impl.c
// C internal implementation, complied with C compiler
_realfunction(float real, float imag); {
  float complex c_complex = real + imag * _Complex_I;
  return realfunction(c_complex);
}

// pure C99 api, not visible to C++ code
realfunction(float complex arg) 
{
//  dostuff
}

```

---

### Post by talonmies on 2011-01-04
The sad reality is that there is no C++ code. This whole exercise is aimed only get getting a c99 code base to compile with a C++ compiler. The compiler in question (the latest Intel offering) includes a compiler assisted parallelisation system called Cilk Plus, and the original poster is convinced that Cilk PLus is the magic bullet that will make the code go fast. Last year he was convinced that Nvidia CUDA was the magic bullet that would make the code code go fast.

---

