---
title: "iostream"
date: 2006-09-25
forum: Programming Talk
---

### Post by Dutchie90 on 2006-09-25
hi,

im using linux for a few days now, and i want to learn c++.. i have some tuts for it, and in those tuts there need to be a file included wich names iostream...
compiling doesn't give any errors, but the app just doesn't start...
i also have tried some examples from an game-engine(irrlicht), and also there only examples wich use iostream don't start. but the compiler just doesn't give me any errors...
is there a solution for this??

--> the code
```

#include <iostream>
using namespace std;

int main ()
{
  cout << "Hello World!";
  return 0;
}

```

--> the makefile
```

CPP = g++

all:
	$(CPP) cpp.cpp -o example $(OPTS)
clean:
	rm example

```

thanks...

---

### Post by amo-ej1 on 2006-09-26
What do you meant with 'don't start' ?

The compilation succeeds without warnings ?  (running 'make all' )
After that does a file called 'example' get created ? What if you type './example' from that current working directory ? What does it print on screen ?

Ah damn, now I see it ;)

New to C/C++ programming error number one: when you type

cout << "Hello";
it prints 'Hello' to the screen but C++/C use internal buffering op output channels, and those streams only get flushed on certain occasions, one occasion is the newline charachter. So you should change that line to:


```

cout << "Hello world\n";

```
(\n == the newline character) or
```

cout << "Hello world" << endl;

```
(endl is defined in the std namespace and expands to the newline character).

---

### Post by thumper on 2006-09-26
The new line character has nothing to do with it.

cout is also flushed when the object is destroyed at program termination.

Since **Dutchie90** is executing his program by clicking on the executable he(she) is not noticing that the program is executing and exiting before they see anything.

In order to see this output, try running it from the command line.

---

