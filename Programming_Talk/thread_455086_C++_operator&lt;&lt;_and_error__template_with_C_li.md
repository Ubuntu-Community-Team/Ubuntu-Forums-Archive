---
title: "C++ operator&lt;&lt; and error:  template with C linkage"
date: 2007-05-26
forum: Programming Talk
---

### Post by mallo on 2007-05-26
Hi everybody,
I have a problem compiling a  file that use a simple .h and its implementation .cpp.
I'm not so good at C programming so this is probably a stupid problem.

I don't understand very well in which file I need to include iostream ( the header in my opinion).
In the attachment there are the examples (the class is based on a similar/identical one on Deitel&Deitel programming book :P).

In a nutshell:

vector2d.h is the interface of vector2d.cpp. The aim is to create a 2d geometrical vector.
test.cpp implements a nutty main().
( Sorry in advance for comments that are in Italian).

I tried to compile it with:
g++ test.cpp -o test
or
g++ test.cpp vector2d.cpp vector2d.h -o test

but there are a lot of errors that look like this:
/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../include/c++/4.1.2/bits/istream.tcc:1254: error: template with C linkage


For the :
vector2d.h:36: error: ISO C++ forbids declaration of ‘ostream’ with no type
you only need to uncomment using namespace std; but the other errors remain.

Anybody knows the correct syntax?:(

---

### Post by rapolas on 2007-05-26
There is nothing wrong with your test.cpp, you can try it commenting that line which includes vector2d.h, and you'll see that everything is fine, but I can't help you with those vector files..

---

### Post by WW on 2007-05-26
In vector2d.h, you declare the class Vector2d--this is C++.  It should not be declared inside the **extern "C" { ... }** environment.  Also, **ostream** is in the **std** namespace, so you must refer to it as **std::ostream** (or put **using namespace std;** at the beginning of your file).

Modified files (just the code sections):

**vector2d.h**
```

#ifndef _VECTOR2D_H
#define _VECTOR2D_H

#include <iostream>

// Vector2d definisce un vettore geometrico 2D

class Vector2d
{
      friend std::ostream &operator<<(std::ostream &, const Vector2d &);
   public:
      Vector2d(float = 0, float = 0);
      void setVector2d(float, float);
      float getX() const { return x; }
      float getY() const { return y; }
   private:
      float x,y;

};

#endif /* _VECTOR2D_H */

```

**vector2d.cpp**
```

#include <iostream>
#include "vector2d.h"

//Costruttore classe Vector2d
Vector2d::Vector2d( float a, float b) { setVector2d(a,b); }

// Set coordinate
void Vector2d::setVector2d(float a , float b)
{
   x=a;
   y=b;
}

// Visualizza Vector2d
std::ostream &operator<< (std::ostream &output, const Vector2d &v)
{
   output << '(' << v.x << ", " << v.y << ')' ;
   return output;
}

```

Compile and run:
```

/tmp$ g++ -Wall -c vector2d.cpp
/tmp$ g++ -Wall -c test.cpp
/tmp$ g++ test.o vector2d.o -o test
/tmp$ ./test
hello world
/tmp$

```

---

### Post by mallo on 2007-05-28
Thanks everybody :)
Thanks WW for the help. the extern "c" was in Anjuta template and I don't know what it does :P...

Bye ;)....

Hope to help someone in future.

---

### Post by hod139 on 2007-05-28
BTW, in header files, you should include
```

#include <iosfwd>

```
instead of iostream.

---

