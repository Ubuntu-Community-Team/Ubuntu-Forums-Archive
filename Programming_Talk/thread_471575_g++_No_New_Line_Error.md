---
title: "g++ No New Line Error"
date: 2007-06-12
forum: Programming Talk
---

### Post by TreeFinger on 2007-06-12
I am learning C++ out of a book meant for windows users. I know my code is right but I still get this error:
```

$ g++ add.cpp -o add.out
add.cpp:24:2: warning: no newline at end of file

```

The program will run fine and everything but this error just irks me ;)

Here is my source code if you would like to check it out:
```

// add.cpp
// Adds two user inputs

#include <iostream>

int main()
{
	int integer1;	// first number to be input by user
	int integer2;	// second number
	int sum;			// sum will be stored in this variable

	std::cout << "Enter first integer\n";	// prompt
	std::cin >> integer1; 						// assigns input to variable integer1

	std::cout << "Enter second integer\n";	// second integer prompt
	std::cin >> integer2;						// assigns input to variable integer2

	sum = integer1 + integer2;	// assignment operator for sum

	std::cout << "The sum of the two numbers is " << sum << "\n"; // Prints the sum of two numbers

	return 0;
	
}

```

I have tried many different things including using std::endl; instead of the escape character but still no luck. Thanks for anyone who takes the time to answer this stupid and pointless question.

---

### Post by Jucato on 2007-06-12
Um... tried putting a blank line after the last } ?

Btw, it's not an error. It's just a warning. An error stops compilation and doesn't let you compile without correcting it. A warning is just that, a warning. It still compiles and runs, as you yourself noticed.

---

### Post by TreeFinger on 2007-06-12
> **Jucato said:**
> Um... tried putting a blank line after the last } ?

...

Yeah, this worked. Boy, do I feel stupid.
Thanks for the tips.

---

