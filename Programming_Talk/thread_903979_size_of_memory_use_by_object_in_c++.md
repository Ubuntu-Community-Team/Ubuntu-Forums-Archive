---
title: "size of memory use by object in c++"
date: 2008-08-28
forum: Programming Talk
---

### Post by monkeyking on 2008-08-28
Hi, is there some way to get the size(physical memory) of a object at runtime?

thanks in advance

---

### Post by cbdonohue on 2008-08-28
I don't think this is addressed in the c standard.  There are functions in linux that help you manage memory, but I'm not sure if there is a way to apply OS commands to this problem

---

### Post by cabalas on 2008-08-28
You can use the size of function found in stdlib.h/cstdlib which will tell you how much memory (in bytes) that a type requires. A link to a reference is

[http://www.itee.uq.edu.au/~comp2303/Leslie_C_ref/C/SYNTAX/sizeof.html](http://www.itee.uq.edu.au/~comp2303/Leslie_C_ref/C/SYNTAX/sizeof.html)

and a trival sample using it is: 

[PHP]
#include <iostream>
#include <cstdlib>

using namespace std;

class foo {
	public:
		foo() { i = 0; b = 0.0; }
		
		int get_num() { return i; }
		void set_num(int n) { i = n; }
	
		float get_float() { return b; }
		void set_float(float f) { b = f; }
	
	private:
		int i;
		float b;
};

int main() 
{
	foo bar;
	cout << "Size of a foo class: " << sizeof(foo) << endl;
	
	return 0;
}
[/PHP]

---

### Post by cbdonohue on 2008-08-28
sizeof() is done at compile tile i believe

---

### Post by cabalas on 2008-08-28
> **cbdonohue said:**
> sizeof() is done at compile tile i believe

You're right. Sorry about that, should have double checked my facts before I made a post.

---

### Post by dribeas on 2008-08-29
> **monkeyking said:**
> Hi, is there some way to get the size(physical memory) of a object at runtime?

thanks in advance

Intrusively (very intrusively, just for debug purposes) you can create a virtual method that will return sizeof() at the lower level of the inheritance hierarchy. Note that for classes that won't be extended you can use a non virtual one. But then again, this means modifying all your code.

---

### Post by mujambee on 2008-08-29
> **monkeyking said:**
> Hi, is there some way to get the size(physical memory) of a object at runtime?

thanks in advance

Not sure what you mean by "at runtime". The size of an object is determined at compile time, and it won't change.

So just using the sizeof operator will get you that.

---

### Post by dwhitney67 on 2008-08-29
> **dribeas said:**
> Intrusively (very intrusively, just for debug purposes) you can create a virtual method that will return sizeof() at the lower level of the inheritance hierarchy. Note that for classes that won't be extended you can use a non virtual one. But then again, this means modifying all your code.
Bear in mind that when declaring a method or destructor as virtual, the class (object) size will increase by 4 bytes.

The extra 4 bytes (maybe 8 on a 64-bit architecture?) is a pointer to the virtual table.

---

### Post by dwhitney67 on 2008-08-29
> **monkeyking said:**
> Hi, is there some way to get the size(physical memory) of a object at runtime?

thanks in advance
As mentioned in previous posts, the sizeof() is probably what you need.

There are cases when the size of a structure (or class object) is not what you would expect.  For instance, if a structure contained two fields, one a char (1 byte) and the other an int (4 bytes).  You would probably surmise that the size of the structure is 5 bytes, however the correct answer is 8 bytes!

The reason is because the compiler is word-aligning the structure in memory.  This "minor detail" confounds some developers, especially when they are working on embedded systems, or on systems where message objects/structures are transmitted from one system to another.

So the best practice is to never assume you know the size of an object.  Always rely on the compiler to tell you by using the sizeof() utility.

---

### Post by mujambee on 2008-08-29
> **dwhitney67 said:**
> 
There are cases when the size of a structure (or class object) is not what you would expect.  For instance, if a structure contained two fields, one a char (1 byte) and the other an int (4 bytes).  You would probably surmise that the size of the structure is 5 bytes, however the correct answer is 8 bytes!


Just to clarify, in most compilers this can be overriden by command line options or pragmas.

---

### Post by Zugzwang on 2008-08-29
It is also worth mentioning that if sizeof(...) return 100 bytes or so, than it might still be that not even a single object of that type fits into memory! This is because of course pointers and also std::whatever constructs are not counted (except from some control information). Example:

[PHP]
class Foo {
private:
  char *c;
public:
   Foo() {
     c = new char[1024*1024*1024];
   }
   ~Foo() { delete[] c; }
};
[/PHP]

The sizeof(Foo) will be 4 bytes in this example but creating an instance of it requiress ~1GB (or more). There is AFAIK no way in C++ to get this interpretation of the size of an object (without changing all your code to provide this information).

---

### Post by nvteighen on 2008-08-29
sizeof() will return the amount of memory something uses in stack. If you happen to use dynamic memory, then the size will be... well... what you're asking to allocate.

So, maybe you could add the result of sizeof() (compile-time defined memory) + the sizes of dynamically allocated members (runtime defined memory).

---

### Post by dwhitney67 on 2008-08-29
> **Zugzwang said:**
> It is also worth mentioning that if sizeof(...) return 100 bytes or so, than it might still be that not even a single object of that type fits into memory! This is because of course pointers and also std::whatever constructs are not counted (except from some control information). Example:

[PHP]
class Foo {
private:
  char *c;
public:
   Foo() {
     c = new char[1024*1024*1024];
   }
   ~Foo() { delete[] c; }
};
[/PHP]

The sizeof(Foo) will be 4 bytes in this example but creating an instance of it requiress ~1GB (or more). There is AFAIK no way in C++ to get this interpretation of the size of an object (without changing all your code to provide this information).
Actually, the size of the object Foo is indeed 4 bytes, regardless of whether the member data 'c' is pointing to a chunk of allocated memory.

If you want to know the size of the data being pointed to by 'c', then write a method to return 1024x1024x1024, or better yet, define a constant to represent that value, and return that (and use the constant when allocating too!).

---

### Post by Zugzwang on 2008-08-29
> **dwhitney67 said:**
> Actually, the size of the object Foo is indeed 4 bytes, regardless of whether the member data 'c' is pointing to a chunk of allocated memory.


Right, I just wanted to point our that the OP probably wants something different than he/she asked for. :-)

---

