---
title: "multiple definition ... template with object files"
date: 2009-03-01
forum: Programming Talk
---

### Post by monkeyking on 2009-03-01
Hi trying to convert on old program of mine,
into templated code I get these error messages like
"multiple definition of ... first defined here"

The problem is that I'm used to using "staged compiling" like
[PHP]
g++ -c file1.cpp
g++ -c file2.cpp
g++ -o prog file3.cpp[/PHP]

But this doesn't seem to be working with multiple templated files,
like
[PHP]
header.hpp : the main templated header
funs.cpp : extra functions using header.hpp, this file is a pragma once[/PHP]

If I at this point create a new file called superclass.cpp with it's header in superclass.h (including funs.cpp), I can compile it with -c
[PHP] g++ -c superclass.cpp[/PHP]

But if I create a runme.cpp file that looks something like

[PHP]
#include "superclass.h"
int main(){
superclass aClass();
}
[/PHP]
The program complains about undefined references if I do
```

g++ runme.cpp

```

If I link the object filed from superclass.o like
[PHP]
g++ runme.cpp superclass.o
[/PHP]
The program complains multiple definitions.

Is it not possible to link together templated files?

thanks in advance

---

### Post by dwhitney67 on 2009-03-01
You have provided insufficient information wrt the header files and .cpp files.  One would need to see the contents to assess why your app is having a multiple-definition error when an attempt to link it is being made.

One thing about templated classes... the implementation _must_ reside in a .h file.  There are two ways to accomplish this:

1)  As you declare the method you can implement it right then and there; or

2)  You can declare the method and then implement it after.

Either way, the declaration and the implementation must be in the header file.

Some developers like to place their method implementations into a file with an extension of ".impl", which is the shorthand notation for implementation.

Here's an example of a header file with a templated class:

Foo.h:
```

#ifndef FOO_H
#define FOO_H

template <typename T>
class Foo
{
  public:
    Foo(const T value);

    T getValue() const;

  private:
    T m_value;
};

#include "Foo.impl"

#endif

```

Foo.impl:
```

template <typename T>
Foo<T>::Foo(const T value ) : m_value(value)
{
}

template <typename T>
T Foo<T>::getValue() const
{
  return m_value;
}

```

Now, wrt compiling multiple modules, you can do it separately as you have shown, or you can compile them all at one time.  If doing them separately, eventually you must use all of the object files (those with the .o extension) to form the executable image.  Here's an example with 3 modules, one of which contains the main() function:
```

g++ -c Module1.cpp
g++ -c Module2.cpp
g++ -c Main.cpp
g++ Module1.o Module2.o Main.o -o myapp

```
Of course, apply whatever CFLAGS and LFLAGS you require.

As for header files containing template code, these are presumably included in one or more of the .cpp files.  You would not compile the header files, nor the .impl files (if used), that contain template code, for these will be compiled when the appropriate .cpp file(s) are compiled.

---

### Post by monkeyking on 2009-03-01
Thanks dwhitney,
you example works.

But mine doesn't work,
I'll have to loook into this...

---

### Post by monkeyking on 2009-03-02
Hi again,
I tracking down the linking error, and it seems that you can't link with specialization.

These are the files, builing on from dwhitneys nice example

it works now, when not linking
'g++ ultra.cpp'

but when changing class1.cpp to class1.h and trying to link it says

```

g++ -c class1.cpp -Wall -g
g++ ultra.cpp -Wall class1.o
class1.o: In function `Foo<float>::getValue() const':
class1.cpp:(.text+0x148): multiple definition of `Foo<float>::getValue() const'
/tmp/ccaGGnzU.o:ultra.cpp:(.text+0x6c): first defined here
class1.o: In function `Foo<int>::getValue() const':
class1.cpp:(.text+0x174): multiple definition of `Foo<int>::getValue() const'
/tmp/ccaGGnzU.o:ultra.cpp:(.text+0x98): first defined here
collect2: ld returned 1 exit status




```
[PHP]
//TempletedFoo.h
#ifndef TEMPLATED_FOO_H
#define TEMPLATED_FOO_H

template <typename T>
class Foo
{
public:
  Foo(const T value);
  T getValue() const;
  
private:
  T m_value;
};
#include "TemplatedFoo.impl"
#endif
[/PHP]

[PHP]
//TemplatedFoo.impl
template <typename T>
Foo<T>::Foo(const T value ) :m_value(value){}

template <>
int Foo<int>::getValue() const
{
	std::cout<<"is int\n";
	  return m_value;
}



template <>
float Foo<float>::getValue() const
{
	std::cout<<"is float\n";
	  return m_value;
}
[/PHP]


[PHP]
//class1.h
#include "TemplatedFoo.h"
class class1{
 public:
  class1(void);
  ~class1(void);
  int dummy_method(void);
  Foo<int> dummy_method2(void);
};
[/PHP]


[PHP]
//class1.cpp
#include <iostream>

#include "TemplatedFoo.h"
#include "class1.h"


class1::class1(void){std::cout << "object constructed" << std::endl;}
class1::~class1(void){std::cout <<"object destructed" << std::endl;}
int class1::dummy_method(void){
  int ret = 2;
  return ret;
}
Foo<int> class1::dummy_method2(void){
  Foo<int> ret(4);
  return ret;
}
[/PHP]


[PHP]
//ultra.cpp
#include <iostream>

#include "class1.cpp" //works when not linking change to .h and complains

int main(){
  std::cout<<"start of main\n";
  class1 cls1;
  std::cout <<"calling dummy method: "<< cls1.dummy_method()<<std::endl;
  Foo<int> var = cls1.dummy_method2();
  std::cout <<"calling dummy method2: " <<var.getValue()<<std::endl;
  std::cout<<"end of main\n";
}
[/PHP]

---

### Post by dwhitney67 on 2009-03-02
> **monkeyking said:**
> ...
[PHP]
//TemplatedFoo.impl
template <typename T>
Foo<T>::Foo(const T value ) :m_value(value){}

template <>
int Foo<int>::getValue() const
{
	std::cout<<"is int\n";
	  return m_value;
}

template <>
float Foo<float>::getValue() const
{
	std::cout<<"is float\n";
	  return m_value;
}
[/PHP]
...
This is wrong; you should only have one definition of getValue().  Please refer back to the example I provided earlier.  You should not need to specialize the method here, or anywhere else for that matter.

---

### Post by monkeyking on 2009-03-02
I agree that in the example provided by you it would make little sense to have a member function specialized.
But sometimes it's very usefull.

But I found a fix, or more like a hack that should fix the problem,
just inlining the member function specialization will fix the linker error, thats.

[PHP]
template <>
inline int Foo<int>::getValue() const
{
    std::cout<<"is int\n";
      return m_value;
}

template <>
inline float Foo<float>::getValue() const
{
    std::cout<<"is float\n";
      return m_value;
}  
[/PHP]

[http://gcc.gnu.org/onlinedocs/gcc/Template-Instantiation.html](http://gcc.gnu.org/onlinedocs/gcc/Template-Instantiation.html)

---

### Post by dwhitney67 on 2009-03-02
Here's some code based on your previous example:

Foo.h
```

#ifndef FOO_H
#define FOO_H

template <typename T>
class Foo
{
  public:
    Foo(const T value);

    T getValue() const;

  private:
    T m_value;
};

#include "Foo.impl"

#endif

```

Foo.impl:
```

template <typename T>
Foo<T>::Foo(const T value) : m_value(value)
{
}

template <typename T>
T Foo<T>::getValue() const
{   
  return m_value;
}

```

Class1.h:
```

#ifndef CLASS1_H
#define CLASS1_H

#include "Foo.h"
#include <string>

class Class1
{
  public:
    Class1();

    Foo<int>         dummyMethod1() const;
    Foo<std::string> dummyMethod2() const;
    Foo<float>       dummyMethod3() const;
};

#endif

```

Class1.cpp:
```

#include "Class1.h"

Class1::Class1()
{
}

Foo<int>
Class1::dummyMethod1() const
{
  return Foo<int>(4);
}

Foo<std::string>
Class1::dummyMethod2() const
{
  return Foo<std::string>("This is a test!");
}

Foo<float>
Class1::dummyMethod3() const
{
  return Foo<float>(10.6);
}

```

Main.cpp:
```

#include "Class1.h"
#include "Foo.h"
#include <iostream>

int main()
{
  Class1           c1;
  Foo<int>         val1 = c1.dummyMethod1();
  Foo<std::string> val2 = c1.dummyMethod2();
  Foo<float>       val3 = c1.dummyMethod3();

  std::cout << val1.getValue() << std::endl;
  std::cout << val2.getValue() << std::endl;
  std::cout << val3.getValue() << std::endl;
}

```

Now this is not hard to understand, is it?

To build:
```

g++ -c Class1.cpp
g++ -c Main.cpp
g++ Main.o Class1.o -o mytest

```

---

### Post by monkeyking on 2009-03-02
It's still correct.

but it will only work if you don't do templated class member function specializations.

consider this implementation.
[PHP]
template <>
inline
Foo<float>::Foo(const float value ) {
std::cout << "I do floats:\n";
  m_value = (value);
	
}

template <>
inline
Foo<std::string>::Foo(const std::string val){
  std::cout << "I don't do strings:\n";
}
template <typename T>
T Foo<T>::getValue() const{
  return m_value;
}
[/PHP]

With and without the inline.

---

### Post by dwhitney67 on 2009-03-02
> **monkeyking said:**
> ...
[PHP]
template <>
inline
Foo<float>::Foo(const float value ) {
std::cout << "I do floats:\n";
  m_value = (value);
	
}

template <>
inline
Foo<std::string>::Foo(const std::string val){
  std::cout << "I don't do strings:\n";
}

...
[/PHP]


I'm confused as to why you feel that you must specialize these methods -- do you like to type a lot?

What happens if I want to specialize Foo to store an object of type MysteryObject... are you going to specialize a getValue() for that object too?  What if I decide to specialize Foo with a STL vector<int> -- I guess another specialized version of getValue() will be needed as well.

If you would just use the generic declaration/implementation of getValue() as I have described earlier, you would not need to specialize the method.  The compiler will take care of the details and generate the appropriate code.  That's why the template code must reside in a header file.

---

### Post by monkeyking on 2009-03-02
Hi thanks for your reply.

That template class I'm doing is a generalized matrix class.
And as such some operators needs to be specialized.


Division among float/doubles is straightforward,
but integer division is somewhat more involved (quotient,remainder).
And math operators doesn't make sense sense for the  string type.

edit:
But also the cout should be somewhat specialized from type to type.

---

### Post by dwhitney67 on 2009-03-02
Ah, got it.  Then I think you should step away from using a templated object, and instead consider defining an abstract interface class, and then define specialized classes that subclass and implement the pure-virtual method(s) of this interface.  But that's my take on it; you do as you please.

P.S.  You can also define a base-class template class (w/ virtual methods), and then subclass from that template class if some particular specialization is needed.

---

### Post by monkeyking on 2009-06-27
Hi sorry for reviving this old thread,
but I was annoyingly sitting with the same problem again.
-----------------------------------------------------------
To avoid the multiple definition in templated classes,
the solution is to make the member method inlined.

Apparantly this for some magic reason resolves the problem,
apart from code refactoring, which really isnt a solution, but a workaround.

Has anyone any idea how a staged compilation can be done?
It seems too awkward that the methods has to be inlined.

Would externing solve the problem, or does anyone know what is done in the official stl, apparantly they don't have this deficienty. 

thanks

---

