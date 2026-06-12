---
title: "[SOLVED] C++: Problem with template in class:"
date: 2008-08-20
forum: Programming Talk
---

### Post by WitchCraft on 2008-08-20
Hi, using g++ I have a problem:

No compiler error, but when I startup the program:

symbol lookup error: /root/Desktop/aladin/libAladin.so: undefined symbol: _ZN10Cnonstdlib4CStrIPKcEESsRKT_


When I copy all the code from Cnonstdlib.cpp to Cnonstdlib.hpp, and remove Cnonstdlib.o from the makefile, then it works, but as soon as I divide in header and cpp, then I get a symbol lookup error... Why???
I checked and copy-pasted the filenames, so their spelling is correct, including capitals/non-capitals.

Is this something like inline functions, where the you must put the implementation to the declaration?

My Makefile:
```

CC	= g++
OBJ	= Cnonstdlib.o Coffsets.o Cthreading.o main.o  
OUT	= libAladin.so

LIBS	= -pthread
CFLAGS	+= -O2 -pipe -Wall

all: $(OUT)
	rm -rf $(OBJ)
%.o: %.c
	$(CC) $(CFLAGS) -fPIC -c -o $@ $<

$(OUT): $(OBJ)
	$(CC) $(LDFLAGS) -fPIC -shared $(OBJ) $(LIBS) -o $(OUT)

clean:
	rm -rf $(OBJ) $(OUT)

```

Cnonstdlib.hpp
```


#ifndef Cnonstdlib_H
#define Cnonstdlib_H


class Cnonstdlib
{
    public:
        Cnonstdlib() ;
        ~Cnonstdlib() ;
        template<typename DataType> std::string CStr(const DataType  &dt_Data);
};

#endif //Cnonstdlib_H


```


Cnonstdlib.cpp
```


#include <iostream>
#include <string>
#include <sstream>

#include "Cnonstdlib.hpp"


Cnonstdlib::Cnonstdlib()
{
}


Cnonstdlib::~Cnonstdlib()
{
}


template<typename DataType>
std::string Cnonstdlib::CStr(const DataType  &dt_Data)
{
	std::stringstream strstrmOutStream ;
	strstrmOutStream << dt_Data ;
	return strstrmOutStream.str() ;
}

```

---

### Post by dwhitney67 on 2008-08-20
Template code must be implemented in the header file.

---

### Post by WitchCraft on 2008-08-20
> **dwhitney67 said:**
> Template code must be implemented in the header file.

Ah, my suspicion was right. Thanks.

---

### Post by dwhitney67 on 2008-08-20
> **WitchCraft said:**
> Ah, my suspicion was right. Thanks.
This same "template" topic was discussed the other day.  Another approach some developers take is to define the templated class, or method(s), in a header file, then implement the templated methods in a separate file.  This file needs to be included within the header file.

For example in Foo.h:
[PHP]#ifndef FOO_H
#define FOO_H

template< class T>
class Foo
{
  public:
    Foo( T value );

    T getValue() const;

    ...

  private:
    T m_value;
};

#include "FooImpl.cpp"

#endif[/PHP]
In FooImpl.cpp:
[PHP]template<class T>
Foo<T>::Foo( T value )
  : m_value(value)
{
}

template<class T>
T Foo<T>::getValue() const
{
  return m_value;
}[/PHP]
In Main.cpp
[PHP]#include "Foo.h"

int main()
{
  Foo<int> foo(5);
  ...
  return 0;
}[/PHP]
To compile:
```
$ gcc Main.cpp -o MyApp
```
The FooImpl.cpp does NOT need to be compiled to generate an object file.

---

### Post by dribeas on 2008-08-21
> **dwhitney67 said:**
> Template code must be implemented in the header file.

Thats the general simple (even if not completely true) rule. More precisely, the template (method in this case) must be instantiated for the given type at some point. Usually that is achieved by defining the method in the header file, but it can also be achieved by explicitly instantiating the template method at some point. The shortcoming here is that you must know in advance all the types you want to instantiate and perform it manually.

```

// test.h
class Test
{
   template <typename T> void f( T const & ); // tell the compiler that it will exist
};
// test.cpp
#include "test.h"
template <typename T> void Test::f( T const & ) // Definition of the implementation
{
   // code
}
// [*]
template void Test::f( double const & ); // Template instantiation for double
template void Test::f( int const & ); // ... for int ...

```

Now all users of class Test will only include the header and the template will only be processed and compiled in one compilation unit (.cpp), lowering compilation times. Note that the header does not include the implementation, only the signature to keep the compiler happy.

The instantiation can also be split in different files. A header file with just the definition, another file (.impl?, .tmpl?) with the real code (up to [*]) and template instantiation .cpp files:

```

// test.h, test.cpp (now test.impl) up to [*] will be the same
// test_int.cpp - Instantiation for int
#include "test.impl"
template void Test::f( int const & );
// test_double.cpp - Instantiation for double
#include "test.impl"
template void Test::f( double const & );

```

Implementation of the methods are gathered from .impl, each template instantiation will be compiled in its own compilation unit.

   David

---

### Post by dribeas on 2008-08-21
> **dwhitney67 said:**
> This same "template" topic was discussed the other day.  Another approach some developers take is to define the templated class, or method(s), in a header file, then implement the templated methods in a separate file.  This file needs to be included within the header file.

Note that in your case, as the only templated code is one method you can define all non-templated code in one .cpp file that is not included from the header and only the templated method in another .cpp/.impl/.tmpl file that is included. Or even push this method up to the header file.

```

// test.h
class Test
{
   Test();
   template <typename T> void f( T const & );
};
#include "test.impl"
// test.impl
template <typename T> void f( T const & ) { ... }
// test.cpp
Test::Test() { ... }

```

Code in test.cpp is compiled once, the template method is compiled in each of the user classes that include test.h and indirectly test.impl.

   David

---

### Post by WitchCraft on 2008-08-22
> **dribeas said:**
> 
 The shortcoming here is that you must know in advance all the types you want to instantiate and perform it manually.


Yes, I took a look at templated classes, but this is exactly what bugged me, because I don't necessarely know it in advance...

> 
```

// test.h, test.cpp (now test.impl) up to [*] will be the same
// test_int.cpp - Instantiation for int
#include "test.impl"
template void Test::f( int const & );
// test_double.cpp - Instantiation for double
#include "test.impl"
template void Test::f( double const & );

```

Implementation of the methods are gathered from .impl, each template instantiation will be compiled in its own compilation unit.

   David


Nice one, I like it, I will use this method.

---

### Post by WitchCraft on 2009-06-06
Actually, in the meantime i found out that this is not true.
 
You can implement a template separate from the header.
 
It's only a question of the syntax.
 
I'll add the method as soon as I retrieve my experimenting class from a backup ;-)

---

