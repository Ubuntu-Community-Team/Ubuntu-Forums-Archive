---
title: "C++ integer problem"
date: 2007-03-15
forum: Programming Talk
---

### Post by MdaG on 2007-03-15
Hi!

I'm wondering if there is a class for handling very large integers and corresponding math operations like +, -, *, /, sqrt etc. ?

I'm currently using "unsigned long long", but it's not enough by far. I want something that can handle arbitrary large integers and preferably be fast as well...

---

### Post by jincast90 on 2007-03-15
> **MdaG said:**
> Hi!

I'm wondering if there is a class for handling very large integers and corresponding math operations like +, -, *, /, sqrt etc. ?

I'm currently using "unsigned long long", but it's not enough by far. I want something that can handle arbitrary large integers and preferably be fast as well...

You should try using float. Although afaik float is not very fast.

---

### Post by duff on 2007-03-15
No.  Try [http://gmplib.org/](http://gmplib.org/) (it's labled in apt as "libgmp3c2")

---

### Post by stchman on 2007-03-15
> **MdaG said:**
> Hi!

I'm wondering if there is a class for handling very large integers and corresponding math operations like +, -, *, /, sqrt etc. ?

I'm currently using "unsigned long long", but it's not enough by far. I want something that can handle arbitrary large integers and preferably be fast as well...


long long is 2^80 which is 1.209 x 10^24

That is a big number.

Anything larger than that you will need to use floats and doubles.

---

### Post by MdaG on 2007-03-15
> **jincast90 said:**
> You should try using float. Although afaik float is not very fast.

I need it to be integers since I need 100% precision. floats can handle large numbers, but are limited to five or six digits of precision.

> long long is 2^80 which is 1.209 x 10^24

That is a big number.
On my machine a "long long" is 2^63 which isn't enough.

> No. Try [http://gmplib.org/](http://gmplib.org/) (it's labled in apt as "libgmp3c2")

Sweet! Will do :-)
Thanks!

*edit*
Having trouble understanding how to use GMP. I can't seem to include 'gmpxx'? (I've installed libgmpxx4)

---

### Post by WW on 2007-03-15
You can also use the C++ library **CLN**: [http://www.ginac.de/CLN/](http://www.ginac.de/CLN/)
Both GMP and CLN are in the repositories.

Here's an example of using CLN, along with some related comments: [http://math.colgate.edu/~wweckesser/software/cln/](http://math.colgate.edu/~wweckesser/software/cln/)
That link includes an example of a program implemented twice, once with CLN and once with GMP.

---

### Post by MdaG on 2007-03-15
Can't seem to make it compile... Here's some code for a sample program trying to solve equations on the form x*x - D*y*y = 1. Where D is an integer > 0 and a solution is only valid if x and y are integers. Needless to say that for some values of D, x and y get very large...

```
#include <iostream>
#include <cln/integer.h>

#define INTEGER cl_I

using namespace std;

// Brute force attempt at finding the minimal solution to the equation x*x - D*y*y = 1
// and finding the D that gives the largest x as its' minimal solution for any D <= 1000.
int main(void) {
	INTEGER	xx, x, y, D, sqrtD, largestX, optimalD;
	bool found;

	largestX = optimalD = 0;
 	for (D = 1; D <= 1000; D++) {
		sqrtD = static_cast<INTEGER>(sqrt(D));
		if (sqrtD*sqrtD == D) {
			D++;				// If D is square no solution exists
		}
		y = 1;
		found = false;
		while (not found) {
			xx = 1 + D*y*y;		// Calculate x*x
			x = static_cast<INTEGER>(sqrt(xx));
			if (x*x == xx) {	// If x is square we have a solution!
				found = true;
				if (x > largestX) {
					largestX = x;
					optimalD = D;
				}
			}
			y++;
		}
		cout << "D = " << D << ", optD = " << optimalD << " --> largestX = " << largestX << endl;
 	}
	cout << "D = " << optimalD << " --> x = " << largestX << endl;
	return 0;
}
```

Trying to compile this gives:
> g++ -o run solution66_slow.cc -lcln
g++: /lib/libcln.a: No such file or directory
solution66_slow.cc:3:25: error: cln/integer.h: No such file or directory
solution66_slow.cc: In function &#8216;int main()&#8217;:
solution66_slow.cc:15: error: &#8216;cl_I&#8217; was not declared in this scope
solution66_slow.cc:15: error: expected `;' before &#8216;xx&#8217;
solution66_slow.cc:18: error: &#8216;largestX&#8217; was not declared in this scope
solution66_slow.cc:18: error: &#8216;optimalD&#8217; was not declared in this scope
solution66_slow.cc:19: error: &#8216;D&#8217; was not declared in this scope
solution66_slow.cc:20: error: &#8216;sqrtD&#8217; was not declared in this scope
solution66_slow.cc:20: error: expected type-specifier before &#8216;cl_I&#8217;
solution66_slow.cc:20: error: expected `>' before &#8216;cl_I&#8217;
solution66_slow.cc:20: error: expected `(' before &#8216;cl_I&#8217;
solution66_slow.cc:20: error: expected `)' before &#8216;;&#8217; token
solution66_slow.cc:24: error: &#8216;y&#8217; was not declared in this scope
solution66_slow.cc:27: error: &#8216;xx&#8217; was not declared in this scope
solution66_slow.cc:28: error: &#8216;x&#8217; was not declared in this scope
solution66_slow.cc:28: error: expected type-specifier before &#8216;cl_I&#8217;
solution66_slow.cc:28: error: expected `>' before &#8216;cl_I&#8217;
solution66_slow.cc:28: error: expected `(' before &#8216;cl_I&#8217;
solution66_slow.cc:28: error: expected `)' before &#8216;;&#8217; token


I get the same result with "g++ solution66_slow.cc -o run -I$CLNDIR/include $CLNDIR/lib/libcln.a".
I'm not sure how to use the sqrt(...) function here. INTEGER used to be "unsigned long long" so don't mind the casting...

---

### Post by WW on 2007-03-15
Don't forget to add this line:
> using namespace cln;

---

### Post by WW on 2007-03-15
Two more comments:
1. To use an expression like D++ in CLN, you will have to put this at the beginning of your program:
> #define WANT_OBFUSCATING_OPERATORS
(Why?  Look here: [http://www.ginac.de/CLN/cln_4.html#SEC43](http://www.ginac.de/CLN/cln_4.html#SEC43) )
2. Replace the line **sqrtD = static_cast<INTEGER>(sqrt(D))** with an appropriate use of either **isqrt** or **sqrtp**: [http://www.ginac.de/CLN/cln_4.html#SEC27](http://www.ginac.de/CLN/cln_4.html#SEC27)

In general, when you are just trying out a new library, keep the documentation handy: [http://www.ginac.de/CLN/cln_toc.html](http://www.ginac.de/CLN/cln_toc.html)

---

### Post by MdaG on 2007-03-15
Added the namespace just below std. Still won't compile. I've installed libcln4 using apt-get...

> $ g++ -o run solution66_slow.cc -lcln
solution66_slow.cc:2:25: error: cln/integer.h: No such file or directory
solution66_slow.cc:7: error: ‘cln’ is not a namespace-name
solution66_slow.cc:7: error: expected namespace-name before ‘;’ token
solution66_slow.cc: In function ‘int main()’:
solution66_slow.cc:12: error: ‘cl_I’ was not declared in this scope
solution66_slow.cc:12: error: expected `;' before ‘xx’
solution66_slow.cc:15: error: ‘largestX’ was not declared in this scope
solution66_slow.cc:15: error: ‘optimalD’ was not declared in this scope
solution66_slow.cc:16: error: ‘D’ was not declared in this scope
solution66_slow.cc:17: error: ‘sqrtD’ was not declared in this scope
solution66_slow.cc:17: error: expected type-specifier before ‘cl_I’
solution66_slow.cc:17: error: expected `>' before ‘cl_I’
solution66_slow.cc:17: error: expected `(' before ‘cl_I’
solution66_slow.cc:17: error: ‘sqrt’ was not declared in this scope
solution66_slow.cc:17: error: expected `)' before ‘;’ token
solution66_slow.cc:21: error: ‘y’ was not declared in this scope
solution66_slow.cc:24: error: ‘xx’ was not declared in this scope
solution66_slow.cc:25: error: ‘x’ was not declared in this scope
solution66_slow.cc:25: error: expected type-specifier before ‘cl_I’
solution66_slow.cc:25: error: expected `>' before ‘cl_I’
solution66_slow.cc:25: error: expected `(' before ‘cl_I’
solution66_slow.cc:25: error: expected `)' before ‘;’ token


---

### Post by WW on 2007-03-15
Also install **libcln-dev**.

---

### Post by MdaG on 2007-03-15
Thank you, I'm almost at the finish line. Just need to figure out how to "cout" the answer and I'm done. :-)

*edit*
[This](http://math.colgate.edu/~wweckesser/software/cln/ammprobcln.cpp) example uses cout with the cl_I as one "usually" does, but this isn't an option for me apparently.

---

### Post by MdaG on 2007-03-17
It working now! :-) 
Not as fast as I'd hoped though, maybe I'm using it in the wrong way? :( 
```
#include <cln/integer.h>
#include <iostream>

using namespace cln;
using namespace std;

// Brute force attempt at finding the minimal solution to the equation x*x - D*y*y = 1
// and finding the D that gives the largest x as its' minimal solution for any D <= 1000.
// Avoiding the solution when x = 1 and y = 0.
// Compile with: g++ -o run solution66_slow.cc -lcln
int main(void) {
	cl_I	xx, x, y, D, sqrtD, largestX, optimalD;
	bool found;

	largestX = optimalD = 0;
 	for (D = 1; D <= 1000; D = D + 1) {
		if (sqrtp(D, &sqrtD)) {
			D = D + 1;				// If D is a perfect square no solution exists -> increment to avoid
		}
		y = 1;
		found = false;
		while (not found) {
			xx = 1 + D*y*y;			// Calculate x*x
			if (sqrtp(xx, &x)) {	// If x*x is a perfect square we have a solution!
				found = true;
				if (x > largestX) {
					largestX = x;
					optimalD = D;
				}
			}
			y = y + 1;
		}
 	}
	cout << "Largest minimal solution is given by D = " << optimalD << ", --> x = " << largestX << endl;
	return 0;
}
```

---

### Post by WW on 2007-03-17
On the slim chance that someone else might try to compile this, I had to change **#include <cln/integer.h>** to **#include <cln/cln.h>** to get the output with cout to work. Apparently the definition of the << operator for CLN objects is not included in cln/integer.h.

It is not surprising that this program to solve Pell's Equation takes a long time.  For some values of D, the smallest solutions are quite large.  For example, the table at [http://mathworld.wolfram.com/PellEquation.html](http://mathworld.wolfram.com/PellEquation.html) shows that for D=61, the smallest integers that solve the equation are x=1766319049 and y=226153980.  So just finding a solution for D=61 will take a pretty long time for your program.  Then consider that you are solving the problem for D up to 1000.  If there are many more values of D that have solutions like D=61,  your program will take a *very* long time.

---

### Post by rplantz on 2007-03-17
> **jincast90 said:**
> You should try using float. Although afaik float is not very fast.

You may wish to read my comments about floats at [http://www.ubuntuforums.org/showthread.php?p=2298433#post2298433](http://www.ubuntuforums.org/showthread.php?p=2298433#post2298433)

---

### Post by MdaG on 2007-03-17
> **WW said:**
> On the slim chance that someone else might try to compile this, I had to change **#include <cln/integer.h>** to **#include <cln/cln.h>** to get the output with cout to work. Apparently the definition of the << operator for CLN objects is not included in cln/integer.h.

It is not surprising that this program to solve Pell's Equation takes a long time.  For some values of D, the smallest solutions are quite large.  For example, the table at [http://mathworld.wolfram.com/PellEquation.html](http://mathworld.wolfram.com/PellEquation.html) shows that for D=61, the smallest integers that solve the equation are x=1766319049 and y=226153980.  So just finding a solution for D=61 will take a pretty long time for your program.  Then consider that you are solving the problem for D up to 1000.  If there are many more values of D that have solutions like D=61,  your program will take a *very* long time.

Yes, you're quite correct. For D = 61 the program takes more than six minutes to compute the answer. For D = 109 it takes more than six hours ! The best way to solve this involves continued fractions. I'd hoped that I'd be able to find the answer within one or two hours, but this brute force approach takes WAAAAAY too long. I just needed to confirm that that was the case which wasn't possible with "regular" int. However solving the first 100 equations (D <= 100) takes approximately 35 sec. on my machine while using cl_I takes approximately 7 min. So maybe it would've been practical to brute force this problem had cln been faster... Anyway, I'm off to solve this using continued fractions. Thanks for the help! :-)

---

