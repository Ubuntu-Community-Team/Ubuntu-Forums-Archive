---
title: "C++ Template Instantiation"
date: 2009-10-01
forum: Programming Talk
---

### Post by kinslayer_e on 2009-10-01
Hi! I'm running Ubuntu 9.04 and using Code::Blocks as C++ IDE. I have the following code:

Temp.h:
```
#ifndef TEMP_H_INCLUDED
#define TEMP_H_INCLUDED

template <typename T>
class Temp {
    public:
        Temp (T d = T(0)): _dato(d) {}

        T    getDato () const;
        void setDato (T d);
    private:
        T _dato;
};

template class Temp<double>;

#endif // TEMP_H_INCLUDED

```

Temp.cpp:
```
#include "Temp.h"

template <typename T>
T Temp<T>::getDato () const { return _dato; }

template <typename T>
void Temp<T>::setDato (T d) { _dato = d; }
```

main.cpp:
```
#include "Temp.h"
#include <iostream>

using namespace std;

int main()
{
    Temp<double> temp(3.24);

    cout << temp.getDato() << endl;
    return 0;
}

```

As you can see, I'm trying to use explicit instantiation of the template in the header file, but when I try to compile, the linker shows me "undefined reference to Temp<double>::getDato() const".
The weird thing is that this code works in Windows with MinGW and GCC. In Ubuntu, it works if I put the template instantiation on the end of the Temp.cpp file.
I know I can / should put all the template's implementation on the header file and that will work, but this is for an university's work and they ask me to separate the implementation.

I'll apreciate any help or explanation!

---

### Post by dwhitney67 on 2009-10-01
I'm an old-school C++ developer, so I don't quite understand the first parts of this statement:
```

template class Temp<double>;

```
What are you doing here?

As for the template implementation, you need to include that within the header file; well, at least that is how I do it.

Something like this would work...

Template.h
```

#ifndef TEMPLATE_H
#define TEMPLATE_H

template <typename T>
class Template
{
public:
   Template(T data) : data(data) {}

   T get() const;
   void set(T d);

private:
   T data;
};

#include "Template.impl"

#endif

```
Template.impl
```

template <typename T>
T Template<T>::get() const
{
   return data;
}

template <typename T>
void Template<T>::set(T d)
{
   data = d;
}

```

Main.cpp
```

#include "Template.h"

int main()
{
   Template<double> td(5.0);

   ...
}

```

P.S.  M$ has their own compiler, GNU has theirs.  You need to find code that works under both.  What I have demonstrated above, barring any syntax errors, will work.

---

### Post by MadCow108 on 2009-10-01
> **dwhitney67 said:**
> I'm an old-school C++ developer, so I don't quite understand the first parts of this statement:
```

template class Temp<double>;

```
What are you doing here?


this instantiates the template in that translation unit.
Unfortunately this doesn't work because it does not have the implementation of the functions when compiling main.cpp.
so you have to instantiate it in temp.cpp for every type you want to use (and so partly defeating why you used templates in the first place) or, how dwhitney suggested, in declare everything in the header.
[http://www.parashift.com/c%2B%2B-faq-lite/templates.html#faq-35.12](http://www.parashift.com/c%2B%2B-faq-lite/templates.html#faq-35.12)

you could solve this by using the export keyword.
But this is (although in the standard since 98 ) only supported by very few compilers and is thus not recommend to use in portable programs.

---

### Post by dribeas on 2009-10-01
The problem is that you are explicitly initializing the class where the compiler does not see the definition of the methods:

```

// Test.h
template <typename T>
struct Test
{
   void print( T );
};

// Test.cpp
#include <iostream>
#include "Test.h"

template <typename T>
void Test<T>::print( T datum )
{
   std::cout << datum << std::endl;
}
template struct Test<double>; // explicit instantiation in cpp

// main.cpp
#include "Test.h"
int main()
{
   Test<double> t; t.print( 5.5 ); // ok
   Test<int> t2; t2.print( 5 ); // link error: Test<int>::print undefined
}

```

---

### Post by TheBuzzSaw on 2009-10-01
When designing templates, put all the code into the header file. It does violate the whole H/CPP separation pattern, but it makes life a lot easier when dealing with templates. It will likely compile if you do that.

---

