---
title: "C++ Pointers confusion"
date: 2008-09-19
forum: Packaging and Compiling Programs
---

### Post by keatonvictor on 2008-09-19
Hi everyone

I am trying to learn C++ and I am on Pointers now. As far as I can see this is correct code, but I keep getting errors for it.

------------------------------------
#include <iostream>
#define NEWLINE '\n'
using namespace std;

int main(){
	int i = 10;
	cout << NEWLINE;
	cout << "Variable i memory location = " << &i;
	cout << NEWLINE;
	cout << "Variable i value =           " << *i;
	cout << NEWLINE; 
	return 0;
}

--------------------------------------------

I keep getting the following error. What am I doing wrong? 

main.cpp: In function ‘int main()’:
main.cpp:10: error: invalid type argument of ‘unary *’
:guitar:

---

### Post by issih on 2008-09-19
Theres an error on this line:

```
cout << "Variable i value = " << *i;
```

you dereference i as if it was a pointer, but it is not, it is merely an int variable...

if you'd done:

```

int i =10;
int * pInt = &i;
cout << "Variable i value = " << *pInt;

```

that would make sense.

also note that the c++ libraries contain the endl operator which gives you a new line if you just do:

```
cout << endl;
```

it also flushes the output buffer just to be complete about things :)

Hope that helps

---

### Post by doorman on 2008-09-19
Hy!

The code is actually wrong :(

when you declare a variable like this:
```
int i = 10;
```just as you did, it is a "normal" variable, whilst
```
int *j = &i;
```is a pointer variable. This means that you can write the following:
```
cout << i;
cout << &i;
cout << j;
cout << &j;
cout << *j;
```The first one prints out the value of "i", the second one prints its address in memory, same as the third cout. The forth cout prints put the address of the variable "j" (which is different from the addess of "i"), while the last one prints out the value of the address which "j" points to (i.e. it prints the value of "i")

Tip: instead of defining the new line each time (which is, btw, platform dependent), you can use "endl", which resides in the std namespace. I.e., you could write
```
cout << i << endl;
```
instead of
```
cout << i << NEWLINE;
```

Hope it helps!

P.S. Pointers are a tricky thing to learn (along with references in C++), but are very helpful in everyday life (especially if you plan on messing around with the kernel source code)

---

