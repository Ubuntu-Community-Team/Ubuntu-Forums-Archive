---
title: "compiling a *.C file with gcc -&gt; error"
date: 2006-02-19
forum: Packaging and Compiling Programs
---

### Post by cvmostert on 2006-02-19
Hi there,

I am trying to compile a simple C++ program with gcc and i get the error:

Look at output.txt file below... could not paste output... too many faces what so ever... :-(


I compiled it on another machine with gcc and it works well... 

i have the build-essential package installed aswell...?

it probably is a simple mistake... here is the program... i am starting to learn to program in C++ :-)

```
// increaser.. using Void!

#include <iostream>
using namespace std;

void increase (void* data, int size)
{
	switch (size)
	{
		case sizeof(char) : (*((char*)data))++; break;
		case sizeof(int) : (*((int*)data))++; break;
	}
}

int main ()
{
	char a = 'x';
	int b = 1602;
	increase (&a,sizeof(a));
	increase (&b,sizeof(b));
	cout << a << ", " << b << endl;
	return 0;
```

---

### Post by jrib on 2006-02-19
Use g++ for compiling c++.  You are missing an ending brace for main, but that probably just got missed in the copy and paste.

```

jasonr@luso:~/devel$ g++ test.cc
jasonr@luso:~/devel$ ./a.out
y, 1603

```
[edit] also I like to name my c++ files .cc or .cpp.  I prefer .cc because it is shorter.  Cap C would confuse me too much :)

---

### Post by cvmostert on 2006-02-19
Thanx for the info, ok... it worked, using g++

but i compiled the program once with gcc... 

does all the programs i compile like you said with g++ give the a.out output file?

i probably have to give them separate names hey?

thank you thus far!

another question:::
i can not compile this program i got from a tutorial on [www.cplusplus.com](www.cplusplus.com)

> g++ 27-pointer-function.C
27-pointer-function.C: In function 'int main()':
27-pointer-function.C:24: error: 'minus' was not declared in this scope


here is the program:
```
// pointer to functions
#include <iostream>
using namespace std;

int addition (int a, int b)
{ return (a+b); }

int subtraction (int a, int b)
{ return (a-b); }

int (*minus)(int,int) = subtraction;

int operation (int x, int y, int (*functocall)(int,int))
{
  int g;
  g = (*functocall)(x,y);
  return (g);
}

int main ()
{
  int m,n;
  m = operation (7, 5, addition);
  n = operation (20, m, minus);
  cout <<n;
  return 0;
}

```

---

### Post by jrib on 2006-02-19
```
g++ file.cc -o runme
```

will make the compiled program called 'runme' instead of a.out.  I'll take a look at your source later during my labshift :)

[edit] as far as compiling c++ with the gcc command, I think it should work since I have read about it.  But I don't know enough to tell you why it isn't working with gcc but with g++ it does.

---

### Post by cvmostert on 2006-02-19
Thank you. Will keep an eye on this forum.

---

### Post by jrib on 2006-02-19
```

// pointer to functions
#include <iostream>
using namespace std;

int addition (int a, int b)
{ return (a+b); }

int subtraction (int a, int b)
{ return (a-b); }


int operation (int x, int y, int (*functocall)(int,int))
{
  int g;
  g = (*functocall)(x,y);
  return (g);
}

//int (*minus)(int,int) = subtraction;  //why doesn't this work here??
int x = 5; //let's see if this works...

int main ()
{
  int m,n;
  int (*minus)(int,int) = subtraction; //let's see if ti works when we declare it inside main
  m = operation (7, 5, addition);
  n = operation (20, m, minus); //yep, no errors...
  cout <<n<< endl << x << endl; //yep x is a global and outputs correctly...
  return 0;
}

```

I don't know enough c++ to tell you why your original doesn't work.  The results of the code above  (which compiles fine) confuse me :)

---

### Post by cvmostert on 2006-02-20
The output is not important, it is just a tutorial.  

and i dont know why 'int (*minus)(int,int) = subtraction;' it does not work globally.

should probably also als the people at [www.cplusplus.com](www.cplusplus.com) or try and compile the program somewhere else... this puts a kind of a stale mate on my c++ learning tutorial...

thanx so far!

---

### Post by Roptaty on 2006-03-12
Try changing minus to something else; for instance minusx. My compiler (gcc 3.4.5) has this to say about the code: 
```

minus.cc:24: error: use of `minus' is ambiguous
minus.cc:11: error:   first declared as `int (*minus)(int, int)' here
/usr/lib/gcc/i686-pc-linux-gnu/3.4.5/include/g++-v3/bits/stl_function.h:143: err                                                    or:   also declared as `template<class _Tp> struct std::minus' here
minus.cc:24: error: `minus' was not declared in this scope

```

---

