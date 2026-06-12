---
title: "Segmentation fault but memory still available!"
date: 2009-03-25
forum: Programming Talk
---

### Post by Astenorh on 2009-03-25
This is more a general linux question. I did a small program in Java and in C++ to compute the Eratosthene Sieve. Java can go up to 10 000 000 but C++ can't.

```

/*
 * Use eratosthen algorithm to find out prime numbers
 */

#include <iostream>

using namespace std;

const long int SIZE = 1000000;

void sieve(long int p);
void init(long int size, bool* array);

int main()
{
	sieve(SIZE);
	return 1;
} 

inline void sieve(long int p)
{
	long int k = 2; 
	bool theSieve[p];
	init(p, theSieve);
	while (k*k < p) 
	{
		if (theSieve[k])
		{
			for (long int i = k*k; i < p; i += k)
			{
				theSieve[i] = 0;
			}
		} 
		k++;
	}
	k = p-1;
	while (!theSieve[k]){
		k--;
	}
	cout << k << endl;
}

inline void init(long int size, bool* array)
{
	for (long int i = 0; i < size; i++)
	{
		array[i] = 1;
	}	
}

```

I have checked the size of the array it is only 1 000 000 bytes and I have more than 3 GB available!

What is the problem? (it still doesn't work if I switch from long ints to ints)

---

### Post by dwhitney67 on 2009-03-25
How did you get this to work?
```

...
	bool theSieve[p];
...

```
If you compile your application with the following g++ options, "-Wall -pedantic -ansi", you will get an error similar to this:
```

test.cpp:3: error: ISO C++ forbids variable length array &#8216;theSieve&#8217;

```

Try this instead to see if your results improve:
```

void sieve(long int p)
{
   ...
   bool* theSieve = new bool[p];
   ...
   cout << k << endl;

   delete [] theSieve;
}

```

---

### Post by johnl on 2009-03-25
> **dwhitney67 said:**
> How did you get this to work?
If you compile your application with the following g++ options, "-Wall -pedantic -ansi", you will get an error similar to this:
```

test.cpp:3: error: ISO C++ forbids variable length array ‘theSieve’

```


variable length arrays were introduced in C99.  gcc will allow you to use this feature in C++ code even though it is not a part of C++98 (unsure about C++0x.)

You can find more information about how it works [here](http://gcc.gnu.org/onlinedocs/gcc/Variable-Length.html).

It's still possible that this is the cause of the problem, of course.

To the original poster:  What exactly is your issue?  I compiled and ran your code as both 32-bit and 64-bit; in both cases I got:

```

ledbettj@reznor:~$ ./test
999983

```

---

### Post by stroyan on 2009-03-25
The way that you allocate your array 'theSieve' you are requesting a
local variable that will be on the stack.  That is a limited resource.
The convention is that programs with big data requirements will allocate
most memory from the heap or mmap regions.  The maximum size of stack
is often kept fairly low.  That can leave more address space available
for other data regions.  It can also catch problems earlier if a program
starts infinite call recursion.

You can see the stack limits that are set for your account by using
"ulimit -s" or "ulimit -a" at the shell prompt.

Allocating with 'malloc' or 'new' will allow you to use up to the
'data seg size' or 'max memory size' reported by "ulimit -a".

---

