---
title: "How do I use GMP?"
date: 2007-05-30
forum: Programming Talk
---

### Post by bns on 2007-05-30
I have written a program in C++.  It works fine for small numbers, but the numbers become large quite quickly.  It seems like the GMP library will do what I need, but I don't really understand how to implement it (I'm really inexperienced).  The manual is difficult to understand, and I was wondering if anyone knows of an understandable howto, or even just a couple of examples of simple code that utilize GMP.

---

### Post by tkjacobsen on 2007-05-31
Note that this was the first time I used gmp, so it might not be perfect or even correct. But it calculates pi correctly to 80 digits (I dont want to  check more)

This is a program calculating pi using the gauss-legendre algorithm. It works with arbitrary precision.

```
#include<gmpxx.h>
#include<iostream>
#include<iomanip>


int main() 
{
	long prec = 1000;
	mpf_set_default_prec(prec);
	
	mpf_class a(1);
	mpf_class b(mpf_class(1)/sqrt(mpf_class(2)));
	mpf_class t(mpf_class(1)/mpf_class(4));
	mpf_class p(1);
	mpf_class x,y,pi;
	
	while ( a - b > mpf_class(1e-1000))
	{
		x = (a + b)/2;
		y = sqrt(a*b);
		t = t - p*(a-x)*(a-x);
		a = x;
		b = y;
		p *=2;
	}
	
	pi =  (a+b)*(a+b)/(mpf_class(4)*t);
	
	std::cout << std::setprecision(80) << pi << std::endl;
	
	return 0;
}

```

To compile:
g++ -lgmp -lgmpxx pi.cpp -o pi


EDIT:
you can find a manual here:
[http://www.gnu.org/software/gmp/manual/](http://www.gnu.org/software/gmp/manual/)

---

### Post by bns on 2007-05-31
Thanks!  I haven't had a chance to look over it yet, but I appreciate it.

---

### Post by WW on 2007-05-31
If you are considering C++, take a look at [CLN]("http://www.ginac.de/CLN/").

---

### Post by bns on 2007-06-01
Thanks, I'll look into it.

---

### Post by bns on 2007-06-01
I got it to work using GMP, thanks for the help.

---

