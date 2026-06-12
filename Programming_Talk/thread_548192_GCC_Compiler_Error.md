---
title: "GCC Compiler Error?"
date: 2007-09-11
forum: Programming Talk
---

### Post by 71fnRVVm on 2007-09-11
Hi everyone,

I'm sitting here writing my first C++ programs on Feisty (I've written C/C++ before, but not on this environment), and I think I have a compiler problem.

I include the appropriate files in my .cpp file:
```

#include <cstdlib>
#include <iostream>

```

But when I compile I get the errors:
```

error:  no newline at end of file
error:  'cout' was not declared in this scope
```

I've double checked, and I believe I have the g++ compilers and libraries installed... and we're talking simple programs here, just some number processing and output to command line (it's for a class)...

Anyways, I assume the "cout" problem is because of a library issue?  I'm not so sure about the "no newline at end of file"... I checked my code and I'm not missing any semicolons or other syntax...  what could that be related to?

I'll even include the code for the program I'm talking about.  It's not tested, obviously, but the idea is to print the next number in a Fibonacci sequence.  I don't really want/need help with the programming logic, I just want to make sure I'm not doing anything syntactically wrong:
```

#include <iostream>
#include <cstdlib>

int main(int argc, char *argv[]) {
	int user_int, fib1, fib2, new_fib;

	// Set first two Fibonacci numbers
	fib1 = 1;
	fib2 = 1;
	
	// Get the user-input integer
	user_int = (int) argv[0];

	// Create Fibonacci sequence up until the user-input integer
	while (fib2 <= user_int) {
		// Slide the numbers one spot left
		new_fib = fib1 + fib2;
		fib1 = fib2;
		fib2 = new_fib;
	}

	// Create the next number in the sequence AFTER the user-input
	new_fib = fib1 + fib2;

	// Output to screen
	cout << "Fibonacci Sequence:  Next-Number-Finder\n\n";
	cout << "User Input: " << user_int << "\n";
	cout << "Next In Sequence: " << new_fib << "\n";

	return(0);
}
```

Thanks in advance

---

### Post by bogolisk on 2007-09-11
> **71fnRVVm said:**
> Hi everyone,

I'm sitting here writing my first C++ programs on Feisty (I've written C/C++ before, but not on this environment), and I think I have a compiler problem.

I include the appropriate files in my .cpp file:
```

#include <cstdlib>
#include <iostream>

```

But when I compile I get the errors:
```

error:  no newline at end of file
error:  'cout' was not declared in this scope
```

I've double checked, and I believe I have the g++ compilers and libraries installed... and we're talking simple programs here, just some number processing and output to command line (it's for a class)...

Anyways, I assume the "cout" problem is because of a library issue?  I'm not so sure about the "no newline at end of file"... I checked my code and I'm not missing any semicolons or other syntax...  what could that be related to?

I'll even include the code for the program I'm talking about.  It's not tested, obviously, but the idea is to print the next number in a Fibonacci sequence.  I don't really want/need help with the programming logic, I just want to make sure I'm not doing anything syntactically wrong:
```

#include <iostream>
#include <cstdlib>

int main(int argc, char *argv[]) {
	int user_int, fib1, fib2, new_fib;

	// Set first two Fibonacci numbers
	fib1 = 1;
	fib2 = 1;
	
	// Get the user-input integer
	user_int = (int) argv[0];

	// Create Fibonacci sequence up until the user-input integer
	while (fib2 <= user_int) {
		// Slide the numbers one spot left
		new_fib = fib1 + fib2;
		fib1 = fib2;
		fib2 = new_fib;
	}

	// Create the next number in the sequence AFTER the user-input
	new_fib = fib1 + fib2;

	// Output to screen
	cout << "Fibonacci Sequence:  Next-Number-Finder\n\n";
	cout << "User Input: " << user_int << "\n";
	cout << "Next In Sequence: " << new_fib << "\n";

	return(0);
}
```

Thanks in advance



just add a newline as the last line of the file.

std::cout ???

---

### Post by 71fnRVVm on 2007-09-11
Oh, well the "new line" ... haha that should have been obvious, I guess.

I tried "std::cout" already but it spits out a bunch of errors, all similar to:
```
fib.cpp:(.text+0xd1): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
```

... so I kinda figured that wasn't a good solution.

---

### Post by geraldm on 2007-09-11
Changing 3 "cout" to "std::cout" works here.
g++ version 4.2
I do hope you were not using gcc, as that has a slew of errors here.

Gerald

---

### Post by 71fnRVVm on 2007-09-11
Oh, how stupid of me.  Let me reboot since I just installed g++ and it doesn't seem to recognize it...

---

### Post by 71fnRVVm on 2007-09-11
Ok, after running the command
```

g++ ./fib.cpp[/cpde]

I got the error
[code]
Unable to exec g++.real:  No such file or directory
```

Just to make sure I wasn't being stupid, I checked man g++, and ran the same command with the '-c' option to see if it made a difference.  Same error.

Any idea what that error means?  I've never seen that before...

---

### Post by 71fnRVVm on 2007-09-11
I fixed the problem after installing g++ through aptitude, rather than through Synaptic...

I don't know why synaptic didn't install it right...

Thanks for the help.

---

### Post by gnusci on 2007-09-11
Use for:

**error:  'cout' was not declared in this scope**

[PHP]
#include <cstdlib>
#include <iostream>

using namespace std;
[/PHP]

and for:

**error:  no newline at end of file**

just go to the end of the file and press <ENTER>.

---

