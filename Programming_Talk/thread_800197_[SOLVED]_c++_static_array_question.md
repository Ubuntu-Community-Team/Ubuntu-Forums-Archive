---
title: "[SOLVED] c++ static array question"
date: 2008-05-19
forum: Programming Talk
---

### Post by RocketRanger on 2008-05-19
Hi

I'm writing a small program for a class and this bit has be stomped. I declaring an array in main, like so:

const int ARRAY_SIZE = 10;
int numberArray[ ARRAY_SIZE ];

Subsequently I would like to pass this information to a function, so I pass the array pointer and size, in order to create a local array in the function of equal size to the one passed, like so

void function(int *array, const int SIZE) {
   int localArray[ SIZE ];

However this last part won't compile with the error that a const size is expected and localArray cannot be initialized with a size of 0.

Can anyone help me with a explanation why this happens and perhaps point me to an alternative solution.

---

### Post by Victor516 on 2008-05-19
The array size can not be variable whose value is set while the program is running. If you would like to be able to create an array and set the array size at runtime lookup and study the new and delete operator. If you would like an example I can give you one.

---

### Post by luisromangz on 2008-05-19
Well, SIZE is not a constant, is a variable parameter of function, so that's why the compiler is complaining about.

---

### Post by dwhitney67 on 2008-05-19
How are you compiling??  What you describe works for me!

I compiled the code below with "g++ -Wall Test.cpp"

Test.cpp:
[PHP]
#include <cstring>
#include <iostream>


void function(int *array, const unsigned int size)
{
  int localArray[ size ];

  memcpy( localArray, array, sizeof localArray );

  for ( unsigned int i = 0; i < size; ++i )
  {
    std::cout << "localArray[" << i << "] = " << localArray[i] << std::endl;
  }
}

int main()
{
  const unsigned int SIZE = 5;

  int array[ SIZE ] = { 10, 20, 30, 40, 50 };

  function( array, SIZE );

  return 0;
}
[/PHP]

---

### Post by JupiterV2 on 2008-05-19
In C++, I would rather use a vector of integers rather than an array. 

A better, C++ example (utilizing the vector STL):

[PHP]#include <iostream>
#include <vector>

#define MAX_VECTOR 10

using std::cout;
using std::endl;

void function(std::vector<int>& v)
{
	int len = v.size();
	cout << "sizeof(vector) = " << len << endl;
	
	while( --len + 1) cout << "v[len] = " << (v.at(len)) << endl;
	
	return;
}

int main(int argc, char** argv)
{
	std::vector<int> vec(MAX_VECTOR, 0);
	
	for(int x = 0; x < vec.size(); x++) vec.at(x) = x;
	
	function(vec);
	
	return 0;
}[/PHP]

---

### Post by dwhitney67 on 2008-05-19
Right you are, albeit off-topic.

---

### Post by Npl on 2008-05-19
> **dwhitney67 said:**
> How are you compiling??  What you describe works for me!

I compiled the code below with "g++ -Wall Test.cpp"

Test.cpp:The C-Standard someday included Arrays with nonconst Size-Intialisers. I dunno which version added it, but if that code works or not is dependend on which standard g++/gcc is configured to use. If you add -ansi im sure it wont compile.

Edit: that feature got added with C99

---

### Post by dwhitney67 on 2008-05-19
I agree.  With an older compiler, the code I presented earlier may not compile.

I am currently using this version of gcc/g++:
```
g++ (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
```

Even with the -ansi option, I was able to compile the code.

---

### Post by Lux Perpetua on 2008-05-19
Try compiling with -pedantic: > *g++ -pedantic test.cpp*
test.cpp: In function ‘void function(int*, unsigned int)’:
test.cpp:7: error: ISO C++ forbids variable-size array ‘localArray’


---

### Post by dwhitney67 on 2008-05-19
[post deleted]

---

### Post by luisromangz on 2008-05-20
So SIZE wasn't a costant after all :P

---

### Post by RocketRanger on 2008-05-20
> **Victor516 said:**
> The array size can not be variable whose value is set while the program is running. If you would like to be able to create an array and set the array size at runtime lookup and study the new and delete operator. If you would like an example I can give you one.

Thank you for poiting me in the right direction. I googled it and ended up with something like
int *local_array = new int[ SIZE ];

and subesequently

delete[] local_array; 

when I'm done. That works perfectly.

Thanks for you help.

---

### Post by RocketRanger on 2008-05-20
> **JupiterV2 said:**
> In C++, I would rather use a vector of integers rather than an array.

A vector seems a bit excessive for a simple integer array. Besides I'm studying for my exams right now and the problem was from one of the tests I have to practice on and libraries was not allowed.


> **dwhitney67 said:**
> How are you compiling??  What you describe works for me!

Well, what can I say. The example you gave me compiled fine. I'm using g++ v4.2.3-ubuntu7 and compiling with the options -Wall and -o.

What seems to be causing the problem is when the array is initialized. If I remove that part of it from the code mine compiles as well. However is it safe to access that array later on then?

I did this:
```

#include <iostream>
using std::endl;		using std::cout;

void fun(int *a, const int S);

int main() {
	const int SIZE = 5;
	int array[ SIZE ] = { 0, 1, 2, 3, 4 };
	
	fun(array, SIZE);
	
	return 0;
}

void fun(int *a, const int S) {
	int la[ S ] = { 0 };

	return;
}

```

---

