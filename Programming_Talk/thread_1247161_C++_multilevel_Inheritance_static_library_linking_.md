---
title: "C++ multilevel Inheritance static library linking issues"
date: 2009-08-22
forum: Programming Talk
---

### Post by sgrao on 2009-08-22
I am trying to create two static libraries, and use both of them to compile an application. The two static libraries are not independent, but have dependencies in terms of inheritance. 

There are 3 classes
A -> abstract class with interface function vfun1() which is pure virtual
B-> implements A

A and B are to be compiled into  library libb.a

C-> implements A but inherits from B

C compiles into library libc.a

application
creates an object of type c using pointers and calls vfun1()

Here is the code

A.hpp
```
#include <iostream>
using namespace std;
#ifndef A_HPP
#define A_HPP
class A{
public:
A(){cout<<"A construct"<<endl;}
virtual ~A() {cout<<"A destruct"<<endl;}
virtual void vfun1()=0;
};
#endif
```B.hpp
```
#include "A.hpp"
#ifndef B_HPP
#define B_HPP
class B:public A{
public:
B(){cout<<"B construct"<<endl;}
~B() {cout<<"B destruct"<<endl;}
void vfun1();
};
#endif
```B.cpp
```
#include "B.hpp"

void  B::vfun1(){
cout<<"yeah I am B"<<endl;
}
```compilation instructions 
g++ -c B.cpp -o B.o
ar rcs libb.a B.o

C.hpp
```

#include "B.hpp"
#ifndef C_HPP
#define C_HPP
class C:public B{
public:
C(){cout<<"C construct"<<endl;}
virtual ~C() {cout<<"C destruct"<<endl;}
void vfun1();
};
#endif
```C.cpp
```
#include "C.hpp"
void C::vfun1(){
cout<<"Yeah I am C"<<endl;
}
```compile C.cpp into a library
g++ -c -static -L -lb C.cpp -o C.o
ar rcs libc.a C.o

Application file
```

#include "C.hpp"

int main()
{
A *aptr = new C;
aptr->vfun1();
delete aptr;
}
```compiling main into an object file

wihtout using libraries directly using object files
g++ main.cpp B.o C.o -o main.cpp  ->WORKS FINE

using libraries
g++ -static main.cpp -L -lb -lc -o main.o 
ERROR

/tmp/ccU8SB2U.o: In function `B::B()':
main.cpp:(.text._ZN1BC2Ev[B::B()]+0x17): undefined reference to `vtable for B'
/tmp/ccU8SB2U.o: In function `B::~B()':
main.cpp:(.text._ZN1BD2Ev[B::~B()]+0xe): undefined reference to `vtable for B'
/tmp/ccU8SB2U.o: In function `C::C()':
main.cpp:(.text._ZN1CC1Ev[C::C()]+0x17): undefined reference to `vtable for C'
collect2: ld returned 1 exit status

I dont know what I am doing wrong when using the static libraries instead, any guidance would be USEFUL

---

### Post by nvteighen on 2009-08-22
Destructors should never be virtual. That's nonsense, as they aren't ever inherited... so you're asking the child class to have an implementation of something it can't have as it is specific of the parent class.

---

### Post by uljanow on 2009-08-22
> **nvteighen said:**
> Destructors should never be virtual. That's nonsense, as they aren't ever inherited... 

That is nonsense. Destructors need to be virtual if you have a virtual method in order to destroy the base class properly.

---

### Post by grayrainbow on 2009-08-22
> **uljanow said:**
> That is nonsense. Destructors need to be virtual if you have a virtual method in order to destroy the base class properly.

If you plan to use some class as base it's good practice ALWAYS to make destructor virtual. Seems you are at same opiniun but...your ~B() is not virtual :)

---

### Post by Habbit on 2009-08-22
Destructors need to be virtual if some instance of class Derived is going to be destroyed through a a Base*. For example:```

Base* ptr = new Derived;
// Use ptr
delete ptr;
```
In this case, if destructors were not virtual, ~Derived() would not be called because the static type of the pointer expression passed to the delete operator is Base*.

As a rule of thumb, if you use polymorphism (i.e. have virtual functions), make your destructors virtual, as you will be adding nearly no overhead (the vtable is already there) and might avoid these kind of hard-to-debug problems.

---

### Post by TheStatsMan on 2009-08-22
> **Habbit said:**
> 

As a rule of thumb, if you use polymorphism (i.e. have virtual functions)

You have to be a bit careful with your wording here, as you are implying you need virtual functions to use polymorhism with c++, which of course is only true is you are using dynamic polymorphism.

---

### Post by nvteighen on 2009-08-23
Ok, I see the point. The issue is that I don't see any sense on any of the practices you are pointing to. Why would you use Base *ptr = new Derived();?? That's an interface violation and should fail on its own, not "solved" by using a virtual destructor.

(*sigh* Common Lisp polymorphism is that much easier...)

---

### Post by TheStatsMan on 2009-08-23
> **nvteighen said:**
> Ok, I see the point. The issue is that I don't see any sense on any of the practices you are pointing to. Why would you use Base *ptr = new Derived();?? That's an interface violation and should fail on its own, not &quot;solved&quot; by using a virtual destructor.

(*sigh* Common Lisp polymorphism is that much easier...)

 This is not that confusing is it (possibly I am confused about what is confusing you). A standard example is Mammal *pdog =new dog, where dog is the the derived class makes sense as a dog is a mammal. That is the whole idea behind dynamic polymorpism in c++, which is it enables pointers in the base class to be assigned to the derived class.

---

### Post by Habbit on 2009-08-23
> **nvteighen said:**
> Why would you use Base *ptr = new Derived();?? That's an interface violation and should fail on its own
Not at all, think about the Java code "Number num = new Integer(1024);". Then you can call methods such as num.toString(). In C++ it's just the same: pointer/reference conversions _up_ the inheritance hierarchy are safe* and automatically performed, while conversions down the hierarchy require either static_cast or dynamic_cast.

* Except that you must never, ever try to use an array of Derived as an array of Base. Be careful, as with dynamically allocated arrays, the language will let you do this abomination without warning, and it will fail horribly (and possibly silently) at runtime.

---

### Post by dribeas on 2009-08-23
To the original question:

Once you have the libraries created (libb.a, libc.a) you can just compile and link the executable with:

```

$ g++ -o exe main.cpp libb.a libc.a

```

I would recommend that you use some higher level mechanism for compiling (I use CMake)

```

$ cat > CMakeLists.txt << EOF
add_library( b STATIC
   B.cpp )
add_library( c STATIC
   C.cpp )
add_executable( exe
   main.cpp )
target_link_libraries( exe # link against libb.a and libc.a
   b c )
EOF
$ cmake .
$ make

```

Notes on other posts:

As some have already pointed out, if there is a change of deleting through a base pointer, you must make the destructor virtual. If the class has virtual methods, you should make the destructor anyway (almost no cost).

Deleting through base pointers is more common than you might initially think. Just think on storing different type of objects in a hierarchy in the same container (by pointer to avoid slicing, google it if you don't know the term). Most uses of dynamic polymorphism are based in this kind of operations (store/treat as base objects instead of the exact derived class).

There is a comment saying that B destructor is not virtual. That is not correct. In C++, when you override a virtual method, the virtual keyword is optional and interpreted as no-op in the derived class. The method will be virtual whether you expliticly declare it or not. I prefer writing the virtual keyword everywhere for other programmers to read, but the compiler does not care:

```

struct Base {
   virtual void f() { std::cout << "Base" << std::endl; }
};
struct Derived : public Base {
   void f() { std::cout << "Derived" << std::endl; } //virtual, even if not declared
};

```

---

### Post by bender1234 on 2009-08-23
I had sort of a simular problem, a bit tired here right now hitting the hay sack so I might have missed something. But if they are all in different libs, and b is dependent on a, and c is on be you have to link them in the order c b a, for some reason with g++.

Maybe there is some flag to prevent this? Just recently moved to linux(well been in and out a couple of times ;) )

That g++ drives me nuts sometimes hehe

---

### Post by MadCow108 on 2009-08-23
those flags are:
g++ -Wl,--start-group *files* -Wl,--end-group
but it has quite high performance costs (while linking)
see more on in: man ld

the problem in op's code actually seems to be the -L flag
if I put an explicit path instead of nothing there it compiles just fine

---

### Post by dribeas on 2009-08-24
> **MadCow108 said:**
> those flags are:
g++ -Wl,--start-group *files* -Wl,--end-group
but it has quite high performance costs (while linking)
see more on in: man ld

the problem in op's code actually seems to be the -L flag
if I put an explicit path instead of nothing there it compiles just fine

I am not a fan of command line compiling for large projects. I tried removing the -L flag with no success and then gave up on that line of reasoning (providing an escape path: cmake). The problem is that -L requires an argument, when you use -L -lb you are actually telling the linker to search for libraries under the '-lb' directory, wich is probably not what you intended.

---

