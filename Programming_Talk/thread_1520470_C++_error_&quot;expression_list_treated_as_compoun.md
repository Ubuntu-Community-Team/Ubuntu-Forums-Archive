---
title: "C++ error: &quot;expression list treated as compound expression&quot;"
date: 2010-06-29
forum: Programming Talk
---

### Post by adasilva on 2010-06-29
Hi, I new to C++, and I am trying to use the gsl libraries for scientific computation. I keep encountering this error while trying to do a simple example of integration:

```
integral.cpp: In function ‘int main()’:
integral.cpp:23: error: initializer expression list treated as compound expression
```

Here is the program I have written to do a simple integration:
```
#include <iostream>
#include <cmath>
#include <gsl/gsl_integration.h>
using namespace std;

double f(double x, void * params);

int main(){
  double result, error;
  int numberEvals;
  double a=1;

  gsl_function F;
  F.function = &f; // F.function is pointed to the address of f
  F.params = &a;   // F.params is pointed to the address of a

  int gsl_integration_qng(&F, 0, 1, 0, 1e-7, &result, &error, numberEvals);

  cout<<"result="<<result<<endl;
  cout<<"error="<<error<<endl;
  cout<<"numberEvals="<<numberEvals<<endl;

  return 0;
}

double f(double x, void * params){
  // params is a pointer to a void variable
  double a=*(double *) params;   
  cout<<"a="<<a<<endl;
  return a*pow(x,2);

```

Line 23 of my code is the one that begins int gsl_integration_qng

I have already tried adding #include <stdint.h>, as suggested in another post about compile errors.

I am using the g++ compiler on Ubuntu.

I would really appreciate any help anyone can give me!

---

### Post by Some Penguin on 2010-06-29
You shouldn't reuse function names as variable names.

---

### Post by adasilva on 2010-06-29
Thanks for the reply, but I don't think I have reused a function name as a variable name. Are you refering to the 
```
F.function = &f
```
As I understand it, I have only referenced the memory address of the function. Is this enough to give an error? 

If so, do you have a suggestion of how I can refer to the function? This is how it is done in the documentation (see [http://www.gnu.org/software/gsl/manual/html_node/Numerical-integration-examples.html](http://www.gnu.org/software/gsl/manual/html_node/Numerical-integration-examples.html)).

---

### Post by tbastian on 2010-06-29
> **adasilva said:**
> 
```

  int gsl_integration_qng(&F, 0, 1, 0, 1e-7, &result, &error, numberEvals);


```


you have to name a variable. eg:

```

int result = gsl_integration_qng(&F, 0, 1, 0, 1e-7, &result, &error, numberEvals);
```

---

### Post by Some Penguin on 2010-06-29
[http://www.network-theory.co.uk/docs/gslref/QNGnonadaptiveGaussKronrodintegration.html](http://www.network-theory.co.uk/docs/gslref/QNGnonadaptiveGaussKronrodintegration.html)

_Function:_ int **gsl_integration_qng** *(const  gsl_function * f, double a, double b,  double epsabs, double epsrel, double * result,  double * abserr, size_t * neval)*

---

### Post by adasilva on 2010-06-30
Thanks, your responses helped me to fix that error. It also turned out that I needed to link the gsl and cblas libraries using
```
g++ -o filename_of_executable -lgsl -lcblas filename.cpp
```

---

