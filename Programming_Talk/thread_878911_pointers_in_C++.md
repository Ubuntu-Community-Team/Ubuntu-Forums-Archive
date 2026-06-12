---
title: "pointers in C++"
date: 2008-08-03
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-08-03
hi

ive found no clear tutorial on how pointers work in C++

are they important or can i skip them?

i realize it is a very challenging language and i would appreciate any links to good tutorials on them

---

### Post by K2712 on 2008-08-03
Pointers are hugely important, as they are necessary for creating some of the most useful abstract data types there are.  Pointers are what make C/C++ so powerful, and while they may be confusing at first, I highly suggest spending some time learning about them.

You could start here:

[http://www.cprogramming.com/tutorial/lesson6.html](http://www.cprogramming.com/tutorial/lesson6.html)

but I would suggest reading several different tutorials to make sure you understand the concept.

Good Luck!

---

### Post by Diabolis on 2008-08-03
Think of memory as a big box subdivided in little boxes. Every time that you create a variable, a int or a char, it is stored in one of those boxes. Then the box is labeled with the name of you variable.

So **int x = 5** would send the number **5** to a random box and it will label it as box **x**.

pointers do the same thing, they point to boxes (memory locations).

---

### Post by Wybiral on 2008-08-03
> **K2712 said:**
> Pointers are what make C/C++ so powerful, and while they may be confusing at first, I highly suggest spending some time learning about them.

I'm not sure I understand how pointers make C++ powerful. If you mean "capable of low-level optimization tricks", then I might agree. Or did you mean "powerful" in terms of expressibility/problem solving?

---

### Post by CptPicard on 2008-08-03
You certainly can't skip pointers, they are essential, but this here is a bit of an overstatement: :)

> **K2712 said:**
>  Pointers are what make C/C++ so powerful, and while they may be confusing at first, I highly suggest spending some time learning about them.

A language needs a way to point by reference and pass by reference. Otherwise all is pass by value which would generally suck (ignoring pure-functional stuff here). The pointer itself is not some magical ingredient that gives C/C++ some special superpowers over other languages, but it is true that both languages would be pretty useless without the concept.

Other languages just for example transparently make everything a reference. :)

---

### Post by Diabolis on 2008-08-03
> **CptPicard said:**
> 
Other languages just for example transparently make everything a reference. :)

Which languages?

---

### Post by CptPicard on 2008-08-03
> **Diabolis said:**
> Which languages?

Java (excluding primitive types), Python, Ruby...

---

### Post by dwhitney67 on 2008-08-03
I think "powerful" can be used in the sense that C++ provides the capabilities of polymorphism.  For me, it is just a nifty convenience.

jimi_hendrix, here's an example:
[PHP]#include <iostream>

class Base
{
  public:
    virtual ~Base() { std::cout << "Base d'tor called." << std::endl; }

    virtual void doSomething() = 0;

  protected:
    Base() { std::cout << "Base c'tor called." << std::endl; }
};


class DerivedOne : public Base
{
  public:
    DerivedOne() { std::cout << "DerivedOne c'tor called." << std::endl; }

    virtual ~DerivedOne() { std::cout << "DerivedOne d'tor called." << std::endl; }

    void doSomething() { std::cout << "DerivedOne::doSomething called." << std::endl; }
};


class DerivedTwo : public Base
{
  public:
    DerivedTwo() { std::cout << "DerivedTwo c'tor called." << std::endl; }

    virtual ~DerivedTwo() { std::cout << "DerivedTwo d'tor called." << std::endl; }

    void doSomething() { std::cout << "DerivedTwo::doSomething called." << std::endl; }
};


int main()
{
  Base *base = new DerivedOne();

  base->doSomething();
  delete base;

  base = new DerivedTwo();

  base->doSomething();
  delete base;

  return 0;
}[/PHP]

---

### Post by Wybiral on 2008-08-03
> **dwhitney67 said:**
> I think "powerful" can be used in the sense that C++ provides the capabilities of polymorphism.  For me, it is just a nifty convenience.

You know... Dynamic languages don't need polymorphism to do stuff like that :)

---

### Post by LaRoza on 2008-08-03
> **K2712 said:**
> Pointers are what make C/C++ so powerful, and while they may be confusing at first, I highly suggest spending some time learning about them.


All hail the mighty pointer!

Honestly, they are just like numerical arrays, nothing special.

---

### Post by pmasiar on 2008-08-03
> **K2712 said:**
> Pointers are what make C/C++ so powerful, 

Pointers are what makes C++ so confusing (and also memory management). It shows C++ as close to C and ASM. Pointer is just address of a memory cell, with sprinkling of type info.

Other more advanced languages use references instead (which add type info) and can accomplish most of same tasks safer (prone to less errors).

As many of us said you before: if you want to progress from simple to complex, learn basics of programming in simpler language, like Python. You can learn variables, scope, functions, OOP, references and all - with friendlier and simpler to use language. Mastering that, learn C, to understand  how to work close to the metal. Only after that it makes sense to target C++, which adds OOP to C-like 'close to the metal' programming.

Or of course you may start from something hard, like a kid wrestler who insist of competing with adults - but don't be surprised if you are beaten up every time :-)

---

### Post by nvteighen on 2008-08-03
> **LaRoza said:**
> All hail the mighty pointer!

[PHP]
void *TheMightyPointer = 0;
[/PHP]

The Mighty Pointer has arrived to the PT... but some silly programmer attempted to deference it and hell! the whole world crashes with a segfault.

OK, more seriously: although it's meant for C, look at this: [http://crasseux.com/books/ctutorial/Pointers.html](http://crasseux.com/books/ctutorial/Pointers.html). I think it should help you in C++, as it's the same concept and the same way to use them.

---

### Post by jimi_hendrix on 2008-08-03
> **pmasiar said:**
> Or of course you may start from something hard, like a kid wrestler who insist of competing with adults - but don't be surprised if you are beaten up every time :-)

every try playing a pick up basketball game at your local Y with people a head taller then you and twice as strong?

but anyway 2nd question:

when would i use pointers?

---

### Post by nvteighen on 2008-08-03
> **K2712 said:**
> Pointers are what make C/C++ so powerful,

No. C is powerful not because of pointers, but because of its hard-core minimalist design that allows huge extensibility.

On C++, as I don't know it, I can't give any opinion.

---

### Post by LaRoza on 2008-08-03
> **jimi_hendrix said:**
> 
when would i use pointers?

When they are needed.

In C++, it seems the use of raw pointers is discouraged. Not being interested in C++, I can't help there.

---

### Post by CptPicard on 2008-08-03
> **nvteighen said:**
> but because of its hard-core minimalist design that allows huge extensibility.


Speak not of hard-core minimalist design and extensibility before you have met a Lisp... :)

> **LaRoza said:**
> 
In C++, it seems the use of raw pointers is discouraged.

Yes. A wrapper should be used that prevents potentially catastrophic resource leakage.

---

### Post by jimi_hendrix on 2008-08-03
> Yes. A wrapper should be used that prevents potentially catastrophic resource leakage.

well i understand this much[PHP]int *pointer;[/PHP]

---

### Post by LaRoza on 2008-08-03
> **CptPicard said:**
> 
Yes. A wrapper should be used that prevents potentially catastrophic resource leakage.

Like a diaper?

---

### Post by jimi_hendrix on 2008-08-03
> **LaRoza said:**
> Like a diaper?

lol

define wrapper please

---

### Post by LaRoza on 2008-08-03
> **jimi_hendrix said:**
> lol

define wrapper please

Instead of doing things directly, have a function that makes it simpler.

---

### Post by nvteighen on 2008-08-03
> **CptPicard said:**
> Speak not of hard-core minimalist design and extensibility before you have met a Lisp... :)

I'll do :) So: let's say C is just minimalist and extensible and we're all happy.

> **jimi_hendrix said:**
> well i understand this much[PHP]int *pointer;[/PHP]

OK, there you have a pointer that is exactly pointing to an unknown place. Wonderful. Why don't you make it point to somewhere defined?

[PHP]
int main(void)
{
    int a = 9;
    int *pointer = &a;

    return 0;
}
[/PHP]

There you have: pointer now points to a (the & prefix operator gives you the address of any variable).

If I happen to do this:
[PHP]
*pointer = 7;
[/PHP]

Then, a = 7, because the * operator tells the pointer to look where it is pointing to (dereference). In the other hand, pointer = 7 would redirect the pointer to memory address 0x000007 (32-bit architecture), possibly making my program crash because of illegal memory access.

So, as a pointer is a variable that holds a memory address, you're able to access that memory location from anywhere the pointer is available... even if you're in a different function, e.g.:

[PHP]
void myfunc(int *pointer_here)
{
    *pointer_here = 7;
}

int main(void)
{
    int a = 9;
    int *pointer = &a;

    myfunc(pointer); 
    /* No * needed, as we're passing a pointer to another pointer. */

    /* What value will a have after calling my_func? Try printing a to
     * screen! (Is it "cout << a << endl;" in C++?) */

    return 0;
}
[/PHP]

Believe me, there's nothing outside this. The usual hard "array = pointer" topic is easily solvable if you understand there are no built-in arrays in C or C++, just pointers with an offset.

---

### Post by CptPicard on 2008-08-03
> **LaRoza said:**
> Like a diaper?

Well, that's the *garbage collection* side of the issue.

---

### Post by DavidBell on 2008-08-03
In this case the 'wrapper' would be a class that frees memory associated with the pointer when it's destroyed. They are usually referred to as smart pointers.

On your original question, yes you have to learn pointers to use C/C++, they are an essential part of the language and you will start seeing lots of them as soon as you start browsing source code. 

There two places you are likely to encounter them often.

1. Allocating variables on the heap instead of the stack (for big arrays etc)
2. As arguments to functions for a couple of reasons. C/C++ function arguments are always 'by value', so if you want to change the value of a variable you have pass it's pointer (which is still passed 'by value' but this in effect gives a 'by reference' argument when you de-reference it). The other thing is if you want to pass a large struct/class to a function a 'by value' argument would need to copy the whole thing, but when you pass it's pointer it's just a four byte memory location.

As noted higher up most languages pass arguments by reference, but C doesn't so you just have to know pointers. C++ introduced reference arguments but you still need pointers say when you have a function that combines 1. and 2. and allocates new memory for you.

HTH DB

---

### Post by jimi_hendrix on 2008-08-03
ok last thing then i think i got it that was a great explination

how would i use pointers to get the value of an int from another class/method that is out of scope

---

### Post by dwhitney67 on 2008-08-03
If you were to call a function or method, and want to access another class object, that class object will either have to be:
[LIST=1]
[*]Passed into the function
[*]Be a globally defined object
[*]Be a static object (this includes singleton objects)
[/LIST]
Item 1 is typically the recommended approach.  Either pass a pointer or a reference to the object that needs to be queried for the "int".

I never recommend Item 2.  It is poor programming/design.

Item 3 should be questioned as to whether the object really needs to be statically defined.  In some cases it is appropriate, in other cases it is not.  Typically in cases where it is not, it is the "fluent" C programmer falling on his/her a$$ with a bad design.

A singleton object should be defined if the object being modelled is a one-of-a-kind entity.  An example would be a Memory-Manager (MM) in an embedded system, where all other class objects would use the MM to request memory (rather than going directly to the heap) for objects they need to allocate.

---

### Post by jimi_hendrix on 2008-08-03
and by "passed into the function" you mean something like
[PHP]#include "stdafx.h"
#include <iostream>
#include <stdio.h>

using namespace std;

int myfunc(int first,int second)
{
	int total = first + second;
	return total;
} 

int main( int argc, char *argv[] )  
{
	int a, b;
	cout << "enter two intergers to be added: " << endl;
	cin >> a >> b;

	cout << myfunc(a,b) << endl;

    return 0; 

}
[/PHP]

where im passing a and b through the function (im teaching my self so my programming vocabulary could be better)

---

### Post by dwhitney67 on 2008-08-03
No, no, no!  What you are doing is passing 'a' and 'b' by value; you are _not_ passing by reference, much less by pointer.

This would be passing by pointer:
[PHP]...

int myfunc(int *first, int *second)
{
    int total = *first + *second;   // must dereference first and second
                                    // to access value at the memory
                                    // location they point to

    *first  /= 2;                // must dereference before assigning
    *second /= 2;                // new value

    return total;
} 

int main( int argc, char *argv[] )  
{
    int a, b;
    cout << "enter two intergers to be added: " << endl;
    cin >> a >> b;

    cout << myfunc(&a, &b) << endl;  // must pass addresses of a and b

    cout << "a = " << a << endl << "b = " << b << endl;

    return 0; 
}[/PHP]
Try running this program, enter some values for 'a' and 'b' as prompted, then see as their values change upon the function, myfunc(), returning.

---

### Post by jimi_hendrix on 2008-08-04
ok thanks

---

### Post by cszikszoy on 2008-08-04
These examples of pointers are pretty trivial.  You will find much use of pointers in C++ when exploring the concepts of dynamic memory allocation and data structures.

 As an (admittedly trivial) example, say you want to create an array but have the size determined at run time, not compile time.

This code will result in a compile error.
```

[COLOR=#000000][COLOR=#0000bb]using namespace std[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#007700]
[/COLOR][COLOR=#0000bb]int main[/COLOR][COLOR=#007700]( [/COLOR][COLOR=#0000bb]int argc[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]char [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]argv[/COLOR][COLOR=#007700][] )  
{
    [/COLOR][COLOR=#0000bb]int a[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]b[/COLOR][COLOR=#007700];
    [/COLOR][COLOR=#0000bb]cout [/COLOR][COLOR=#007700]<< [/COLOR][COLOR=#dd0000]"Enter array size: " [/COLOR][COLOR=#007700]<< [/COLOR][COLOR=#0000bb]endl[/COLOR][COLOR=#007700];
    [/COLOR][COLOR=#0000bb]cin [/COLOR][COLOR=#007700]>> [/COLOR][COLOR=#0000bb]a[/COLOR][COLOR=#007700];

    [/COLOR][COLOR=#0000bb]int array[a];[/COLOR][COLOR=#007700]

    return [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]; 
}  [/COLOR][/COLOR]

```To properly do this, you would need to use pointers:
```

[COLOR=#000000][COLOR=#0000bb]using namespace std[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#007700]
[/COLOR][COLOR=#0000bb]int main[/COLOR][COLOR=#007700]( [/COLOR][COLOR=#0000bb]int argc[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]char [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]argv[/COLOR][COLOR=#007700][] )  
{
    [/COLOR][COLOR=#0000bb]int a[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]b[/COLOR][COLOR=#007700];
    [/COLOR][COLOR=#0000bb]cout [/COLOR][COLOR=#007700]<< [/COLOR][COLOR=#dd0000]"Enter array size: " [/COLOR][COLOR=#007700]<< [/COLOR][COLOR=#0000bb]endl[/COLOR][COLOR=#007700];
    [/COLOR][COLOR=#0000bb]cin [/COLOR][COLOR=#007700]>> [/COLOR][COLOR=#0000bb]a[/COLOR][COLOR=#007700];

    [/COLOR][COLOR=#0000bb]int *array = new int[a];[/COLOR][COLOR=#007700]

    return [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]; 
}  [/COLOR][/COLOR]

```Pointers are also useful for passing arrays to functions.  In this case you aren't actually passing an array, but a reference to the first element of that array.


Also, depending on whether you are programming in C or C++, void pointers can also be useful for implicit type conversion.  I believe void pointers are illiegal in ANSI C++, but most compilers will only show a warning, and allow the program to compile anyways.

If you want to learn more about the true usefulness of pointers, beyond trivial examples of passing values to a function, research the topic of Data Structures in C++.  Or you could just read any book written by Stroustrup.  (This one is one of my personal favs: [http://www.amazon.com/Annotated-C-Reference-Manual/dp/0201514591/ref=sr_1_6?ie=UTF8&s=books&qid=1217856450&sr=1-6](http://www.amazon.com/Annotated-C-Reference-Manual/dp/0201514591/ref=sr_1_6?ie=UTF8&s=books&qid=1217856450&sr=1-6))

---

### Post by Wybiral on 2008-08-04
> **cszikszoy said:**
> ```

[COLOR=#000000][COLOR=#0000bb]using namespace std[/COLOR][COLOR=#007700];
[/COLOR][COLOR=#007700]
[/COLOR][COLOR=#0000bb]int main[/COLOR][COLOR=#007700]( [/COLOR][COLOR=#0000bb]int argc[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]char [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000bb]argv[/COLOR][COLOR=#007700][] )  
{
    [/COLOR][COLOR=#0000bb]int a[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000bb]b[/COLOR][COLOR=#007700];
    [/COLOR][COLOR=#0000bb]cout [/COLOR][COLOR=#007700]<< [/COLOR][COLOR=#dd0000]"Enter array size: " [/COLOR][COLOR=#007700]<< [/COLOR][COLOR=#0000bb]endl[/COLOR][COLOR=#007700];
    [/COLOR][COLOR=#0000bb]cin [/COLOR][COLOR=#007700]>> [/COLOR][COLOR=#0000bb]a[/COLOR][COLOR=#007700];

    [/COLOR][COLOR=#0000bb]int *array = new int[a];[/COLOR][COLOR=#007700]

    return [/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]; 
}  [/COLOR][/COLOR]

```

And this is what a memory leak looks like :)

---

### Post by cszikszoy on 2008-08-04
> **Wybiral said:**
> And this is what a memory leak looks like :)

Memory deallocation is also an important subject with regards to pointers.

---

### Post by hod139 on 2008-08-04
> **Wybiral said:**
> And this is what a memory leak looks like :)

Where's the leak?  The program allocates an array, ends, and the OS cleans up the used memory:twisted:

---

### Post by Jessehk on 2008-08-04
Wrapper:

```

#include <iostream>

#include <boost/shared_ptr.hpp>

typedef boost::shared_ptr<int> IntPtr;

int main() {
    IntPtr ptr( new int( 32 ) );
    std::cout << *ptr << std::endl;

    ptr = IntPtr( new int( 42 ) );
    std::cout << *ptr << std::endl;
}

```

It's not pretty, but it works.

---

### Post by jimi_hendrix on 2008-08-04
thanks all...i kinda sorta understand it now

ive been told these are the hardest thing in C++

---

### Post by lisati on 2008-08-04
> **Diabolis said:**
> Think of memory as a big box subdivided in little boxes. Every time that you create a variable, a int or a char, it is stored in one of those boxes. Then the box is labeled with the name of you variable.

So **int x = 5** would send the number **5** to a random box and it will label it as box **x**.

pointers do the same thing, they point to boxes (memory locations).
This brought back memories of a course I was on way back in 1979. The lecturer was demonstrating how computers do their stuff using a "pigeon hole" computer. 

> **K2712 said:**
> Pointers are hugely important, as they are necessary for creating some of the most useful abstract data types there are.  Pointers are what make C/C++ so powerful, and while they may be confusing at first, I highly suggest spending some time learning about them.
  
Pointers are useful to know something about. If you ever look to learning ASM in the future it will be essential if you're to understand the different addressing modes available. (Whether or not someone will actually ***need*** ASM in their everyday programming tasks is another story.)

> **LaRoza said:**
> All hail the mighty pointer!

Honestly, they are just like numerical arrays, nothing special.
Nicely said!

---

### Post by jimi_hendrix on 2008-08-04
> **lisati said:**
>  If you ever look to learning ASM in the future it will be essential if you're to understand the different addressing modes available. (Whether or not someone will actually ***need*** ASM in their everyday programming tasks is another story.)


```
mov ax, 9
mov bx, 100
mul ax,bx
```

hehe ASM gives me a headache

---

### Post by Wybiral on 2008-08-04
> **hod139 said:**
> Where's the leak?  The program allocates an array, ends, and the OS cleans up the used memory:twisted:

Yeah, in this example... But I wouldn't recommend getting into that habit :p anyway. It should be second-nature to free memory in C and C++.

---

### Post by jimi_hendrix on 2008-08-04
well i dont know enough to make a leak or to clean it up other then using ints instead of floats for things like basic interger adding

---

### Post by cszikszoy on 2008-08-04
> **jimi_hendrix said:**
> well i dont know enough to make a leak or to clean it up other then using ints instead of floats for things like basic interger adding

Using ints vs floats has nothing to do with creating or cleaning up memory leaks.  Integers and floats are just data types.  They describe the type of data that goes into these variables.  They also determine how arithmetic operations are performed.

---

### Post by jimi_hendrix on 2008-08-04
right but if i have a large program and use just floats it would take more memory

---

### Post by cszikszoy on 2008-08-04
> **jimi_hendrix said:**
> right but if i have a large program and use just floats it would take more memory

Not true.  The compiler is what actually decides how bit an integer or float is.  I believe that on the x86 (intel, amd, etc) architecture that floats are 32 bits wide, and so are ints.  Normally an int is the natural size of the hardware (in the case of x86 architecture, this is 32 bits).

However, as I've said, the size of the data types is entirely left up to the compiler.  For example, I do a lot of embedded development using atmel microprocessors.  On these 8 bit microcontrollers, the size of an integer is 8 bits.

I strongly encourage you (and anyone else coming from a CS background) to truly learn what a microprocessor is.  Learn how it works, learn how memory allocation works, learn what a freaking *register* is.  Learn what assembly is.  This is the background to everything, and this is where everything comes from.  With everything that you learn, you always start from the bottom and work your way up.  I mean you weren't reading Shakespeare in Kindergarten. And likewise, you shouldn't approach learning programming from the top down either.

---

### Post by dwhitney67 on 2008-08-04
> **jimi_hendrix said:**
> right but if i have a large program and use just floats it would take more memory
Keep this simple program in your "back pocket" so that you won't forget the size of typical data types on your system.
[PHP]#include <iostream>

int main()
{
  std::cout << "size of bool: " << sizeof(bool) << std::endl;
  std::cout << "size of char: " << sizeof(char) << std::endl;
  std::cout << "size of unsigned char: " << sizeof(char) << std::endl;
  std::cout << "size of short: " << sizeof(short) << std::endl;
  std::cout << "size of unsigned short: " << sizeof(unsigned short) << std::endl;
  std::cout << "size of int: " << sizeof(int) << std::endl;
  std::cout << "size of unsigned int: " << sizeof(unsigned int) << std::endl;
  std::cout << "size of long: " << sizeof(long) << std::endl;
  std::cout << "size of unsigned long: " << sizeof(unsigned long) << std::endl;
  //std::cout << "size of long long: " << sizeof(long long) << std::endl;
  std::cout << "size of float: " << sizeof(float) << std::endl;
  std::cout << "size of double: " << sizeof(double) << std::endl;

  struct SomeStruct
  {
    char field1;
    char field2;
    int  field3;
  };

  std::cout << "size of SomeStruct: " << sizeof(SomeStruct) << std::endl;

  return 0;
}[/PHP]

Btw, the SomeStruct will be reported as having a size of 8 bytes, not the expected 6.  The reason is because the compiler will allocate space for it such that it sits on a word-aligned boundary.  Sometimes to mitigate anyone having confusion, it is sometimes helpful to add an extra field(s) at the beginning (sometime at the end) of the structure to explicitly show the desired size for the structure.

So:
[PHP]struct SomeStruct
{
  char spare[2]; // spares to explicitly align struct to word-boundary

  char field1;
  char field2;
  int  field3;
};[/PHP]

---

### Post by cszikszoy on 2008-08-04
Unsigned numbers and signed numbers take up exactly the same number of bits in memory.  The difference is the way you represent a negative number in binary.  Again, it's about learning the basics.

In binary, the MSB (most significant bit) is the sign bit in a number.  Therefore, in a signed integer (assuming an int is 32 bits), the range of values you can store are -2^31 -> +2^31.  For unsigned int, you can store the values 0 -> 2^32.

---

### Post by pmasiar on 2008-08-05
> **cszikszoy said:**
> Unsigned numbers and signed numbers take up exactly the same number of bits in memory.  The difference is the way you represent a negative number in binary.  Again, it's about learning the basics.

In binary, the MSB (most significant bit) is the sign bit in a number.  Therefore, in a signed integer (assuming an int is 32 bits), the range of values you can store are -2^31 -> +2^31.  For unsigned int, you can store the values 0 -> 2^32.

yes, so if you don't have negative numbers, you fit **twice as much** unsigned integers (record ID or stufff) than plain positive integers in the same space :-)

---

### Post by Sockerdrickan on 2008-08-05
No, but you can assign one to a really high value.

---

### Post by lisati on 2008-08-05
> **jimi_hendrix said:**
> ```
mov ax, 9
mov bx, 100
mul ax,bx
```

hehe ASM gives me a headache
That takes me back. How about a 32-bit effort, like 
```
move eax,9
mov ebx, 100
add eax,ebx

```
(I haven't done any 32-bit ASM programming for the x86, I must locate the book I have that touches on it and brush up)

---

### Post by jimi_hendrix on 2008-08-05
> **lisati said:**
> 
```
move eax,9
mov ebx, 100
add eax,ebx

```


i dont understand that at all

im assuming ur adding ebx and eax to equal 109

---

### Post by DavidBell on 2008-08-08
> **dwhitney67 said:**
> This would be passing by pointer:
int myfunc(int *first, int *second)
{
    int total = *first + *second;
    *first  /= 2;
    *second /= 2;
    return total;
} 



dwhitney, just curious/clarifying for jimihendrix, I know you did that to illustrate pointers, but nine times out of ten I would have used references for that function. ie
[PHP]
int myfunc(int &first, int &second)
{
    int total = first + second;
    first  /= 2;
    second /= 2;
    return total;
}
[/PHP]

I have sort of general rule that unless the function really needs pointers I use references because they are safer (eg 2nd & 3rd lines of this function could cause damage with undefined pointers).

DB

---

### Post by techmarks on 2008-08-08
> I have sort of general rule that unless the function really needs pointers I use references because they are safer (eg 2nd & 3rd lines of this function could cause damage with undefined pointers).




I also use references for function most of the time.
I wish C would have references.

It's usually good to remember the 3 important atrributes of every pointer, the location, the contents and the indirect value of the pointer.

---

### Post by howlingmadhowie on 2008-08-08
> **CptPicard said:**
> Speak not of hard-core minimalist design and extensibility before you have met a Lisp... :)


i'll meet your lisp and raise you a forth

---

### Post by howlingmadhowie on 2008-08-08
> **jimi_hendrix said:**
> i dont understand that at all

im assuming ur adding ebx and eax to equal 109

the intel x86 has (a rather small number of) registers to store (whole) numbers for use in calculations. the registers have the rather snappy names eax, ebx, ecx...

mov stores a 32 bit number where it's told to, in this case 9 in eax (don't worry about the way the target is before the number, that depends upon the dialect of assembly you're writing in. in particular, gas (the gnu assembler) does it the other way round: movl $9, %eax)

i'll grant you three guesses what add does :)

---

### Post by dwhitney67 on 2008-08-08
> **DavidBell said:**
> dwhitney, just curious/clarifying for jimihendrix, I know you did that to illustrate pointers, but nine times out of ten I would have used references for that function. ie
[PHP]
int myfunc(int &first, int &second)
{
    int total = first + second;
    first  /= 2;
    second /= 2;
    return total;
}
[/PHP]

I have sort of general rule that unless the function really needs pointers I use references because they are safer (eg 2nd & 3rd lines of this function could cause damage with undefined pointers).

DB
When I write C++ code, 9.1 times out of 10 I use references... even sometimes when I still need to pass a pointer!

For instance (and this is a silly example):
[PHP]
...

void function( SomeObject *& obj )
{
  ...
}

int main()
{
  SomeObject *object = 0;

  function( object );

  ...
}
[/PHP]
In most instances, passing by reference is preferable.  It prevents the callee of a function from passing a void-type object, or a non-expected object type, or a 0 (NULL).  It does _not_ however prevent the callee from passing a NULL value via a dereferenced pointer!  So be careful of that when you write your code.

For example:
[PHP]#include <iostream>

class SomeObject
{
  public:
    virtual void print() { std::cout << "SomeObject.print() called." << std::endl; }
};

void function( SomeObject &obj )
{
  obj.print();    // Oops!  A crash will occur here.
                  // The only way to guard against this is to check
                  // the address of obj, either manually using if-statement
                  // or using assert().
}

int main()
{
  SomeObject *obj = 0;

  function( *obj );

  return 0;
}[/PHP]

---

### Post by nvteighen on 2008-08-08
> **dwhitney67 said:**
> 
It does _not_ however prevent the callee from passing a NULL value via a dereferenced pointer!  So be careful of that when you write your code.


Which leads us to well-known principle that anyone will always be able to do silly things with little effort.

---

### Post by DavidBell on 2008-08-08
> **dwhitney67 said:**
> It does _not_ however prevent the callee from passing a NULL value via a dereferenced pointer!

The thing I like about using reference arguments is the compiler will complain if you give it a plain pointer. You can get around that with dereferencing, but you are first going to ask yourself *why* the function is asking for references in the first place and hopefully avoid errors.

DB

---

