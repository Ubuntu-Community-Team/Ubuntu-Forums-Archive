---
title: "[SOLVED] Trouble with g++ compiling modified headers"
date: 2008-01-30
forum: Programming Talk
---

### Post by run4flat on 2008-01-30
I have a problem that is irking me to no end.  Just for background - I am a grad student writing software to simulate an acoustical system.

I'll describe the basic problem and show my code below.  I have a class (called testheader) with a header file and an implementation file.  Some of the functions are very short so I write them as inlines in the header file.  However, if I modify an inline function in the header file and recompile, the changes are not reflected in the output.

Now for the details.  Here's the header file, testheader.hpp:
```

// testheader.hpp

#include <iostream>
using namespace std;

class testheader
{
public:
	testheader() {cout << "Creating a testheader object.\n";}
	~testheader() {cout << "Deleting a testheader object.\n";}
	void act();
};

```

Next the implementation file, testheader.cpp:
```

// testheader.cpp - implimentation of testheader class

#include "testheader.hpp"

void testheader::act()
{
	cout << "testheader acting\n";
}

```

Finally, a driver program in test.cpp:
```

#include "testheader.hpp"

int main()
{
	testheader myTH;
	myTH.act();
	return (0);
}

```

Good.  Now, compile and run:
```

g++ -Wall -c testheader.cpp
g++ -Wall -c test.cpp
g++ -Wall testheader.o test.o -o test
./test

```

The output is what we would expect:
```

Creating a testheader object.
testheader acting
Deleting a testheader object.

```

OK.  *Now modify testheader.hpp*:
```

// testheader.hpp

#include <iostream>
using namespace std;

class testheader
{
public:
	testheader() {cout << "Creating a testheader object[COLOR="Red"] (foo)[/COLOR].\n";}
	~testheader() {cout << "Deleting a testheader object.\n";}
	void act();
};

```

Compile and run:
```

g++ -Wall -c testheader.cpp
g++ -Wall testheader.o test.o -o test
./test

```

Here's the result:
```

Creating a testheader object.
testheader acting
Deleting a testheader object.

```

No foo!

To take it further, let's modify testheader.cpp (keeping testheader.hpp in its modified state):
```

// testheader.cpp - implimentation of testheader class

#include "testheader.hpp"

void testheader::act()
{
	cout << "testheader acting (foo)\n";
}

```

Again, compile and run:
```

g++ -Wall -c testheader.cpp
g++ -Wall testheader.o test.o -o test
./test

```

We get:
```

Creating a testheader object.
testheader acting (foo)
Deleting a testheader object.

```

Still no foo for the inline function!

Does anybody know why this is happening?  Is g++ doing some sort of behind-the-scenes caching or optimization?

---

### Post by run4flat on 2008-01-30
Well, I feel a little sheepish.  I kept calling them inline functions, but it never occurred to me that the compiler would compile them inline.  Of course, you have to recompile the running program to get the results:

```

g++ -Wall -c test.cpp
g++ test.o testheader.o -o test
./test

```

Results in:
```

Creating a testheader object (foo).
testheader acting (foo)
Deleting a testheader object.

```

I suppose the moral of the story is to have a smart makefile so that any implementation files that call the inline functions have a dependence on the header containing the inline functions.

Ugh.  Sorry.

---

