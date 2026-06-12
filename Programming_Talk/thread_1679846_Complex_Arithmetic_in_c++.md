---
title: "Complex Arithmetic in c++"
date: 2011-02-01
forum: Programming Talk
---

### Post by newport_j on 2011-02-01
If you have a line of code that compiles in a c program that looks like this:
 
 
k1 = a1 * (1.0 + -delta*I);
 
with complex.h as an added header file.
 
What is the equivalent in c++ and what additional header files must be added at the beginning of the function? 
 
I have asked people here and no one seems to know. I used the Dr. Dobb's article on complex arithmetic in c and c++ many times, but it is no help here.
 
Just what is the c++ equivalent?
 
Any help apppreciated. Thanx in advance.
 
 
N_j

---

### Post by talonmies on 2011-02-01
Impossible to say. What types are each variable declared as?

---

### Post by worksofcraft on 2011-02-01
[php]

// g++ complex2.cpp
#include <iostream>
#include <complex>

// define a type that uses double precision to represent complex numbers
typedef std::complex<double> complex_double;

// define I... not sure there may be one already... but here is another
const complex_double I(0.0, 1.0);

int main() {
	// initialized with some arbitrary values
	complex_double k1(1,2);
	complex_double a1(3,4);
	double delta = 5.0;

	k1 = a1 * (1.0 + -delta*I);

	std::cout << "k1=" << k1 << std::endl;
	return 0; // oops almost forgot this
}
[/php]

---

### Post by newport_j on 2011-02-01
OK:
 
k1 and a1 are double_complex (as defined in the Dr. Dobb's article), and delta is a double. I thougt this was already up, but it was not so here it is now.
 
N_j

---

### Post by talonmies on 2011-02-01
OK so something like this:

```
k1 = a1 * (1.0 + -delta*std::complex(0.,1.));
```

or alternatively

```
k1 = a1 * std::complex(1., -delta);
```

should work assuming I is the C99 defined imaginary unit.

---

### Post by newport_j on 2011-02-02
When I add the recommened changes to my code I get the following error:
 
[FONT=Courier New][SIZE=3]: error: missing template arguments before ‘(’ token[/SIZE][/FONT]
 
[FONT=Courier New]it is clearly referring to the line where I put in[/FONT]

[FONT=Courier New]k1 = a1 * (1.0 + - delta*std::complex(0.,1.)[/FONT]

[FONT=Courier New]My guess is that I need to put an additonal file in. Would it be cstido stdio.h?[/FONT]

[FONT=Courier New]N_j[/FONT]

---

### Post by worksofcraft on 2011-02-02
> **newport_j said:**
> When I add the recommened changes to my code I get the following error:
 
[FONT=Courier New][SIZE=3]: error: missing template arguments before &#8216;(&#8217; token[/SIZE][/FONT]
 
[FONT=Courier New]it is clearly referring to the line where I put in[/FONT]

[FONT=Courier New]k1 = a1 * (1.0 + - delta*std::complex(0.,1.)[/FONT]

[FONT=Courier New]My guess is that I need to put an additonal file in. Would it be cstido stdio.h?[/FONT]

[FONT=Courier New]N_j[/FONT]

Yes, you should try the example I posted earlier that shows you how to do and you can just copy and paste the whole thing into a file called complex2.cpp and compile that :P

p.s. if in your C program you conditionally define:
```

typedef complex complex_double;

```
you might be able to make it compile with both C and C++ but you will have to take out the C++ style stream and replace it with a printf of your own ;)

---

### Post by talonmies on 2011-02-02
> **newport_j said:**
> When I add the recommened changes to my code I get the following error:

[FONT=Courier New]My guess is that I need to put an additonal file in. Would it be cstido stdio.h?[/FONT]

It was a little test, you failed. Right above it was the correct way to instantiate the std complex type. Did you notice it?

Soln:
```
k1 = a1 * std::complex<double>(1., -delta);
```

---

### Post by newport_j on 2011-02-04
When I saw the code and compared it to mine it seemed that using <iostream> was not needed. Afterall, the function that I worked on did not have cin or cout so why use <iostream>?
 
When I copied and ran the sample code it ran and it proved to me that <iostream> was indeed needed. 
 
It seems counter-intuitive to have the include file <iostream> when you have no file inputs or outputs (cin or cout).
 
As I said that was the missinig include file that made the program work and made the <iostream> incluson onvious.
 
But still it seems counterintuitive.
 
N_j

---

### Post by worksofcraft on 2011-02-04
> **newport_j said:**
> When I saw the code and compared it to mine it seemed that using <iostream> was not needed. Afterall, the function that I worked on did not have cin or cout so why use <iostream>?
 
When I copied and ran the sample code it ran and it proved to me that <iostream> was indeed needed. 
 
It seems counter-intuitive to have the include file <iostream> when you have no file inputs or outputs (cin or cout).
 
As I said that was the missinig include file that made the program work and made the <iostream> incluson onvious.
 
But still it seems counterintuitive.
 
N_j

You don't actually need iostreams, but printf has not got a format specifier for complex numbers and so you have to print thier real and imaginary parts explicitly like this:
[php]
// g++ complex2.cpp
#include <stdio.h>
#include <complex>

// define a type that uses double precision to represent complex numbers
typedef std::complex<double> complex_double;

// define I... not sure there may be one already... but here is another
const complex_double I(0.0, 1.0);

int main(int argc, char *argv[], char *envp[]) {
	complex_double k1(1,2);
	complex_double a1(3,4);
	double delta = 5.0;

	k1 = a1 * (1.0 + -delta*I);
	return !printf("k1=(%f,%f)\n", k1.real(), k1.imag());
}
[/php]

---

