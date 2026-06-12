---
title: "C++ operator overloading..."
date: 2009-07-18
forum: Programming Talk
---

### Post by C++buntu on 2009-07-18
Hi everyone, 

I try to overload the >> operator like this:

```

std::istream& operator>>(std::istream& _Is, const Complex0& _cArg)
{
	std::cout << "Real: ";
	_Is >> _cArg.mdX;
	std::cout << "Imaginary: ";
	_Is >> _cArg.mdY;

	return _Is;
}

```

but in my test code i receive the following C2679 error: binary >> : no operator found which takes a right-hand operand of type const double...

This is my test code:

```

#include <iostream>
#include "ex07ch11file3.h"	// class Complex0

signed int main(void)
{
	using namespace std;

	Complex0 a(3.0, 4.0);
	Complex0 c;
	cout << "Enter a complex number (q to quit):\n";
	while (cin >> c)
	{
		cout << "c is " << c << endl;
		cout << "complex conjugate is " << c.Conj() << endl;
		cout << "a is " << a << endl;
		cout << "a + c is " << a + c << endl;
		cout << "a - c is " << a - c << endl;
		cout << "a * c is " << a * c << endl;
		cout << "2*c is " << 2*c << endl;
		cout << "Enter a complex number (q to quit): ";
	}
	cout << "Done!\n";

	return 0;

}

```

Any suggestions?

---

### Post by doas777 on 2009-07-18
I think you need to cast your numerics as strings in your cout statements.

your trying an op like double << string, but there is no operator defined.

just to check, is this homework, or self study?

---

### Post by C++buntu on 2009-07-18
Why? The >> operator normally can read double values...

---

### Post by doas777 on 2009-07-18
just reading the error message. look for a spot in the code where you have a const double on the right side of a << and you will find a likely target for debugging.

EditL crap, it's >>. sry bout that. well same principal.

---

### Post by C++buntu on 2009-07-18
It's for self study, i'm learning C++ with the C++ Primer Plus book of Stephen Prata.

---

### Post by C++buntu on 2009-07-18
Well, i found the problem...
in my definition of >> overloading, i need to erase the const prefix.

Thanks for the help

---

### Post by MadCow108 on 2009-07-18
you probably are writing a own complex class for a reason
but note that c++ has a standard complex class which can do most operations needed (including overloaded operators)

[http://www.cplusplus.com/reference/std/complex/](http://www.cplusplus.com/reference/std/complex/)

---

### Post by dwhitney67 on 2009-07-18
> **C++buntu said:**
> Well, i found the problem...
in my definition of >> overloading, i need to erase the const prefix.

Thanks for the help
I've made the same mistake before, scratched my head for over an hour, only to realize that I had a typo.

When you are inputting, you can't have a const object; however, when you output you should (but it is not required).

---

### Post by C++buntu on 2009-07-19
> **MadCow108 said:**
> you probably are writing a own complex class for a reason
but note that c++ has a standard complex class which can do most operations needed (including overloaded operators)

[http://www.cplusplus.com/reference/std/complex/](http://www.cplusplus.com/reference/std/complex/)

Yeah, i know :) 
It's the purpose of the programming problem to implement a partially complex math class...

---

### Post by C++buntu on 2009-07-19
> **dwhitney67 said:**
> I've made the same mistake before, scratched my head for over an hour, only to realize that I had a typo.

When you are inputting, you can't have a const object; however, when you output you should (but it is not required).

Yup! That's why i've done here ;).

---

