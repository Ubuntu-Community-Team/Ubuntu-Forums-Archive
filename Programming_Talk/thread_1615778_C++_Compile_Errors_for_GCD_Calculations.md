---
title: "C++ Compile Errors for GCD Calculations"
date: 2010-11-07
forum: Programming Talk
---

### Post by abclemons on 2010-11-07
This is my first foray into programming. My university requires we take a C++ class, but I haven't gone through it yet. However, I got into a class, numerical analysis and methods, which requires a basic knowledge of C++. Thus I got the book C++ for Mathematicians by Scheinermann to self-study before next semester. I ask you to please be patient... I'm a noob programmer. 

I'm in chapter three, and we're writing a program to calculate the GCD of using two known integers. The author says this route is inefficient but that he will continue to refine it. Now, for the error: 
```
aaron@hpdv9005us:~/Documents/C++ Programs$ g++ gcd.cc gcd-tester.cc -o gcd-tester
gcd-tester.cc: In function &#8216;int main()&#8217;:
gcd-tester.cc:18: error: &#8216;gcd&#8217; was not declared in this scope

```

Here's the code for the gcd.h, gcd.cc, and gcd-tester.cc:

**gcd.h**
```
#ifndef GCD_H
#define GCD_H

/**
  * Calculate the greatest common divisor of two integers.
  * Note: gcd(0,0) will returm 0 and print an error message
  * @param a the first integer
  * @param b the second integer
  * @return the greatest common divisor of a and b
  */

long gcd(long a, long b);

#endif
```

**gcd.cc**
```
#include "gcd.h"
#include <iostream>
using namespace std;

long gcd(long a, long b) {

	// if a and b are both zero, print an error and return 0
	if ( (a==0) && (b==0) ) {
		cerr << "WARNING: gcd called with both arguments equal to zero."
		     << endl;
	return 0;
}

	// make sure a and b are both positive
	if (a<0) {
	  a = -a;
	}
	if (b<0) {
	  b = -b;
	}

	// if a is zero, the answer is b
	if (a==0) {
	  return b;
	}
	
	// otherwise check all possibilities from 1 to a

	long d; // d holds the answer

	for (long t=1; t<=a; t++) {
	  if ( (a%t==0) && (b%t==0) ) {
	    d = t;
	  }
	}

	return d;
}
```

**gcd-tester.cc**
```
#include "gcd.h"
#include <iostream>
using namespace std;

/**
  * Evaluates the gcd procedure
  */

int main() {
long a,b;

cout << "Enter the first denominator --> ";
cin >> a;
cout << "Enter the second denominator --> ";
cin >> b;

cout << "The gcd of " << a << " and " << b << " is "
     << gcd(a,b)  << endl; 
return 0;

}
```

I've done checked the code a few times, and it's copied exactly from what's in the book. From what little I know about C++, I don't think the code is the problem. I do think that the way I'm compiling it through g++ may be an issue. Any suggestions?


Regards,

Aaron

---

### Post by Arndt on 2010-11-07
> **abclemons said:**
> This is my first foray into programming. My university requires we take a C++ class, but I haven't gone through it yet. However, I got into a class, numerical analysis and methods, which requires a basic knowledge of C++. Thus I got the book C++ for Mathematicians by Scheinermann to self-study before next semester. I ask you to please be patient... I'm a noob programmer. 

I'm in chapter three, and we're writing a program to calculate the GCD of using two known integers. The author says this route is inefficient but that he will continue to refine it. Now, for the error: 
```
aaron@hpdv9005us:~/Documents/C++ Programs$ g++ gcd.cc gcd-tester.cc -o gcd-tester
gcd-tester.cc: In function ‘int main()’:
gcd-tester.cc:18: error: ‘gcd’ was not declared in this scope

```

Here's the code for the gcd.h, gcd.cc, and gcd-tester.cc:

**gcd.h**
```
#ifndef GCD_H
#define GCD_H

/**
  * Calculate the greatest common divisor of two integers.
  * Note: gcd(0,0) will returm 0 and print an error message
  * @param a the first integer
  * @param b the second integer
  * @return the greatest common divisor of a and b
  */

long gcd(long a, long b);

#endif
```

**gcd.cc**
```
#include "gcd.h"
#include <iostream>
using namespace std;

long gcd(long a, long b) {

	// if a and b are both zero, print an error and return 0
	if ( (a==0) && (b==0) ) {
		cerr << "WARNING: gcd called with both arguments equal to zero."
		     << endl;
	return 0;
}

	// make sure a and b are both positive
	if (a<0) {
	  a = -a;
	}
	if (b<0) {
	  b = -b;
	}

	// if a is zero, the answer is b
	if (a==0) {
	  return b;
	}
	
	// otherwise check all possibilities from 1 to a

	long d; // d holds the answer

	for (long t=1; t<=a; t++) {
	  if ( (a%t==0) && (b%t==0) ) {
	    d = t;
	  }
	}

	return d;
}
```

**gcd-tester.cc**
```
#include "gcd.h"
#include <iostream>
using namespace std;

/**
  * Evaluates the gcd procedure
  */

int main() {
long a,b;

cout << "Enter the first denominator --> ";
cin >> a;
cout << "Enter the second denominator --> ";
cin >> b;

cout << "The gcd of " << a << " and " << b << " is "
     << gcd(a,b)  << endl; 
return 0;

}
```

I've done checked the code a few times, and it's copied exactly from what's in the book. From what little I know about C++, I don't think the code is the problem. I do think that the way I'm compiling it through g++ may be an issue. Any suggestions?


Regards,

Aaron

I guess there is some discrepancy between what you posted and what you tried to compile. When I compile your code, I succeed.

---

### Post by Tony Flury on 2010-11-07
It is definitely not a very efficient method for finding the GCD

in python - I use : 

```

    def _gcd(self,a,b):
        """ gcd(a,b) - finds the greatest common divisor between a & b
        a & b are both non negative Integers
        returns a non negative Integer """
        if b==0 :
            return a
        return self._gcd(b,a % b)

```

the % operator is the modulus operator - I must confess i am not sure why it works - but it does.

---

