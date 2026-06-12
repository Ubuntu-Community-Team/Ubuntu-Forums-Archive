---
title: "array size limitation, c++"
date: 2007-01-09
forum: Programming Talk
---

### Post by dming on 2007-01-09
Hi All,

I install ubuntu recently and am a new-hand at it. To test the gcc compiler, I wrote (between the two dash lines):

----------------------------------------------------------------------
#include <iostream.h>
#include <math.h>

int main()
{
  const int nat=1000,ndim=nat*nat;
  double a[ndim];
  int  i;
  double rr,one=1.;
 
  i=ndim;
  while (i>1){
    rr=rand();
    a[i]=rr/(RAND_MAX+one);
    i--;
  }

  i=ndim;
  while (i>1){
    printf ("RAND_NUMBER> %10d  %25.16f\n", i, a[i]);
    i--;
  }

  return 0;
};
------------------------------------------------------------------------

It runs good at nat=1000; However, when I increase nat to nat=1100, it reported  "Segmentation fault". What puzzled me is that why c++ compiler can only handle such a small size1D  array.  I had also test similar Fortran code in this machine. It works even at nat=15000.

My machine has 2.0G memory, the cpu is Intel Pentium D. The c++ compiler is "GNU C++ Compiler 4;4.0.3-1".

Could anyone give some idea why the array size limitation is so small with this c++ compiler:confused: 

Thank you very in advance.

Ming

---

### Post by Wybiral on 2007-01-09
I'm not sure why that code doesn't work, but, it is a weird mix of C and C++...

But, it will hold that many elements in an array...

```

#include <iostream>

#define nat 1100*1100

using namespace std;

double a[nat];

int main(){
	for(int i = 0; i<nat; i++){
		a[i] = i;
	}

	for(int i = 0; i<nat; i++){
		cout << a[i] << endl;
	}
}

```

So it has to be something with that code.

---

### Post by olejorgen on 2007-01-09
I'm not sure how to fix this for "stack arrays" (probably some compiler flag), but you could try allocating the array on the heap. ie. double a = new double[ndim]; ... delete [] a;

---

### Post by cabalas on 2007-01-09
To be honest the code presented in the op should Seg fault even when the nat  is 1000, this is becuase you are accessing memory which isn't part of the array, as array's go from 0 to upper limit - 1, e.g. if you have an array of size 5 you can access elements 0 through 4. So if you change it so i = ndim - 1 and have the loop go while i > 0, you should be fine

---

### Post by Wybiral on 2007-01-09
> To be honest the code presented in the op should Seg fault even when the nat is 1000, this is becuase you are accessing memory which isn't part of the array, as array's go from 0 to upper limit - 1, e.g. if you have an array of size 5 you can access elements 0 through 4. So if you change it so i = ndim - 1 and have the loop go while i > 0, you should be fine

Nice eye... It should start those little loops with "ndim-1"

BTW, a for loop would probably be a little simpler...

```

for(int i=ndim-1; i>=0; i--){
    rr=rand();
    a[i]=rr/(RAND_MAX+one);
}

```

---

### Post by dming on 2007-01-09
Thank you, Wybiral. You code works with even nat=15000 for my machine. It comes from the differences of claiming the array.   --Ming

---

### Post by Arndt on 2007-01-10
> **dming said:**
> Thank you, Wybiral. You code works with even nat=15000 for my machine. It comes from the differences of claiming the array.   --Ming

Generally, one can't assume that the stack can house as much data as the heap. I don't know about C++, but in C, the stack may be very tiny or even nonexistent (on embedded processors, for example). Even on larger machines, the processor or the operating system may impose a limit, which the compiler implementor has to obey. I suppose that the documentation for each compiler states how big the stack can be, and if perhaps the limit can be increased at compile/link time.

This is the reason why recursive functions of indefinite depth are a bad idea in C or C++. Programming languages which explicitly encourage recursion work by in fact not using the processor stack as their stack, but putting their stack on the heap.

---

