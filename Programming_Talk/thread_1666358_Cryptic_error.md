---
title: "Cryptic error"
date: 2011-01-13
forum: Programming Talk
---

### Post by newport_j on 2011-01-13
The following error is seeen when I compile the function
 
 
 
[SIZE=3][FONT=Courier New]zsigmpr.c:105: error: cannot convert ‘std::complex<double>’ to ‘double’ in assignment[/FONT][/SIZE]
 
[FONT=Courier New]The code in question is now shown.[/FONT]
 
```

[FONT=Courier New][FONT=Courier New][SIZE=3]RSIGMPV =  5.0 * DELTA * SIGMA2 * (CTMP * conj(CTMP)) * SINTH2 /[/SIZE][/FONT]
[SIZE=3][FONT=Courier New] (NU * 2.30259 * (PTHETA * conj(PTHETA)) * cimag(PTHETA) );[/FONT][/SIZE]
[/FONT]
```
 
 
[FONT=Courier New][FONT=Courier New]I believe it is having trouble with the function conj. Line 105 is the first line that runs over to two lines.[/FONT]
 
[FONT=Courier New]The error stated is somewhat cryptic since it refers to complex double which I have defined. What does this mean? How do I fix this?[/FONT]
 
[FONT=Courier New]Anyhelp appreciated. Thanx in advance.[/FONT]
 
 
[FONT=Courier New]Newport_j[/FONT]
[/FONT]

---

### Post by talonmies on 2011-01-13
It probably means RSIGMPV has been declared as a double, but the RHS of the expression resolves to be a complex<double> value, probably because CTMP is a complex<double>.

Of course this is just a wild guess because you haven't bothered to show any of the relevant bits of code.

---

### Post by Vox754 on 2011-01-13
> **newport_j said:**
> The following error is seeen when I compile the function
 
 
 
[SIZE=3][FONT=Courier New]zsigmpr.c:105: error: cannot convert ‘std::complex<double>’ to ‘double’ in assignment[/FONT][/SIZE]
 
[FONT=Courier New]The code in question is now shown.[/FONT]
 
...

Why do you keep altering the font and size?!

WHY?!

Explain.

---

### Post by worksofcraft on 2011-01-13
> **newport_j said:**
> The following error is seeen when I compile the function
  
[SIZE=3][FONT=Courier New]zsigmpr.c:105: error: cannot convert ‘std::complex<double>’ to ‘double’ in assignment[/FONT][/SIZE]
 ...


That is because there is a bug in your code: The C++ compiler is not psychic and so it doesn't know if you want the real or the imaginary component of your complex result... I don't either TBH, but if you do it as follows at least compiles and runs ;)

[php]
// g++ double_trouble.cpp
#include <cstdio>
#include <complex>
using namespace std;

complex<double> cimag(complex<double> iVal) {
	return iVal;
}

int main(int argc, char *argv[], char *envp[]) {
	double DELTA = 1.0;
	double SIGMA2 = 2.0;
	complex<double> CTMP(3, 4);
	complex<double> SINTH2(5, 6);
	double NU = 7.0;
	complex<double> PTHETA(8, 9);

	double RSIGMPV =  (5.0 * DELTA * SIGMA2 * (CTMP * conj(CTMP)) * SINTH2 /
		(NU * 2.30259 * (PTHETA * conj(PTHETA)) * cimag(PTHETA) )).real();

	return !printf("RSIGMPV=%f\n", RSIGMPV);
}
[/php]

---

### Post by newport_j on 2011-01-26
The line in question does compile in c, but not in c++. It gives the error that is shown above.
 
So why c and not c++?
 
N_j
 
Yes, I have asked some programmers and they are not sure of the answer.

---

### Post by talonmies on 2011-01-26
Because C++ doesn't know how to implicitly cast from complex<double> to double. C99 will presumably return the real part of the complex type, C++ makes no such assumptions.

EDIT: The C99 standard says this (§ 6.3.1.7 para 2):
> When a value of complex type is converted to a real type, the imaginary part of the
complex value is discarded and the value of the real part is converted according to the
conversion rules for the corresponding real type.
That is why it works in C99.

---

### Post by newport_j on 2011-01-26
Can I put a conditional around the line that compiles in c and its counterpart that compiles in c++? 
 
That way the code would compile in either c or c++.
 
It would be just an if-then-else conditional. 
 
Thanx in advance.
 
 
N_j

---

### Post by talonmies on 2011-01-26
Why don't you try it out yourself and see?

---

### Post by newport_j on 2011-01-28
I got this program to compile and run, but only using std_cstdio.h, not cstdio.h. I could not find cstdio.h on my hard drive. When I searched the drive for cstdio.h the only file that came up is std_cstdio.h. I tried that file, it worked and the program gave the right answer on execution.
 
If I used just csdtio.h, I got the message, cstdio.h not found. These must be the same file, but their names are slightly different.
 
What does 
 
using name space std 
 
mean?
 
N_j

---

### Post by Arndt on 2011-01-28
> **newport_j said:**
> I got this program to compile and run, but only using std_cstdio.h, not cstdio.h. I could not find cstdio.h on my hard drive. When I searched the drive for cstdio.h the only file that came up is std_cstdio.h. I tried that file, it worked and the program gave the right answer on execution.
 
If I used just csdtio.h, I got the message, cstdio.h not found. These must be the same file, but their names are slightly different.
 
What does 
 
using name space std 
 
mean?
 
N_j

It's not a good idea to hunt for internal files in the language implementation and make your program depend on them.

The suggestion was to use <cstdio>, not <cstdio.h>. Try the former.

---

### Post by newport_j on 2011-01-28
I will. Thank you.
 
N_j

---

### Post by talonmies on 2011-01-28
> **newport_j said:**
> I got this program to compile and run, 
Congratulations. How long did this whole tortuous process take in the end? Two months?
 
> If I used just csdtio.h, I got the message, cstdio.h not found. These must be the same file, but their names are slightly different.In C++, the standard library headers are import without any extension, like
```
import <cstdio>
import <complex>
``` etc. That is why cstdio.h doesn't work.


> What does 
 
```
 using name space std 
```mean?It roughly translates to  "add the contents of the C++ namespace std to the namespace of the current code", and std is the namespace of the C++ standard library. Otherwise you would need to prefix all the standard library calls with the namespace, like

```
std::complex<double> a;
std::printf("testing 123\n");

```

---

