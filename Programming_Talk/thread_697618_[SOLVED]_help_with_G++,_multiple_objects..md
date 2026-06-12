---
title: "[SOLVED] help with G++, multiple objects."
date: 2008-02-15
forum: Programming Talk
---

### Post by Xnyper on 2008-02-15
I am taking a C++ class, and since I'm a Linux user (though just recently) I decided that I should be able to do everything, and more, that the windows users in the class can do, on my Ubuntu box.  Not only that, but I can do it with style--command line style.  I've been writing the code in vim, and compiling it with g++.  No problems until now.  

I have succeeded in compiling the object separately

g++ -c classNameImp.cpp

and then compiling my code and linking it with said object

g++ -Wall progName.cpp className.o

(forgive me if my syntax is slightly inaccurate, I had it right at the time, but don't have anything to compile right now--so I can't test the validity of my examples.  I assume you get the idea.)


My teacher has us use, in situations like the one above, three separate files.  There is the header file (className.h), the implementation file (classNameImp.cpp), and the program file (progName.cpp, this one includes main() )  I'm not sure if this is standard procedure or not, so I thought I'd make note of it.  Also, since its an online class I don't spend much time communicating about code, its just me and the book, so if I say something in a weird way, please let me know.


OK, to question 1.

Say I have a class "point"
and another, "circle"

I want to use an object of type: point in my definition for the class circle (specifically as its centerpoint.)  a.k.a class composition.
I will make a program called "test" to test these classes.

I know that I need to #include"circle.h" at the top of test.cpp, but where do I #include point.h?  Does it go in circle.h? circleImp.cpp? both?

also, when compiling this, do I compile circleImp.cpp and pointImp.cpp separately (using "g++ -c <filename>") or can I compile them both into one object, or will the compiler know to include the information for the class: "point" when I compile the circle.cpp based on the #include statements?  

Finally, if I do compile the classes into separate *.o files, what is the syntax of the g++ command to link multiple objects?

My book spends 4 pages on class inheritance and less than a paragraph on class composition--and my teacher is lost without her beloved windows-based IDE.  So as you can imagine, its a tricky thing to stumble through on your own. Thanks for your help,

---

### Post by hod139 on 2008-02-15
Given this code:
```

#pragma once
#include "point.h"

class circle{
 public:
   void circleFunc() const;
 private: 
   point aPoint;
};

```in file circle.h

```

#include "circle.h"
#include <iostream>

void circle::circleFunc() const{
  std::cout << "In Circle Function\n";
}

```in file circle.cpp

```

#pragma once

class point{
 public:
   void pointFunc() const;
};

```in file point.h

```

#include "point.h"
#include <iostream>

void point::pointFunc() const{
  std::cout << "In Point Function\n";
}

```in file point.cpp

```

#include "circle.h"
#include "point.h"

int main(){
  point aPoint;
  circle aCircle;

  aPoint.pointFunc();
  aCircle.circleFunc();

  return 0;
}

```in file circleTest.cpp

To compile
```

g++ -Wall -o circleTest circleTest.cpp point.cpp circle.cpp

```where -Wall enables all warnings, and -o names the executable circleTest.

If you really want to produce individual object files:
```

g++ -Wall -c circleTest.cpp
g++ -Wall -c circle.cpp
g++ -Wall -c point.cpp
g++ -o circleTest circleTest.o circle.o point.o

```As projects get large, consider looking into using makefiles to manage the build.

**Edit:** Forgot to mention, the #pragma directive is a non-standard way of preventing header files from being included multiple times.  Almost all compilers support this directive though, and I find the syntax cleaner than include guards.

---

### Post by Zwack on 2008-02-15
The one issue that I was going to mention that hod139 missed was that if the header for circle references something public about circle that requires point then you should probably include point.h in circle.h rather than in circle.cpp.  If it only uses it privately then you should include it in circle.cpp rather than circle.h.

In other words if something uses circle and the public definition of circle includes point then you need to include the definition of point whenever you include the definition of circle to make sure that they have all of the information that they need as it is possible that they don't need to know about point themselves.  The easiest way to do that is to have the header file include other relevant header files... And yes you need some way of making sure that the header file is only really included once.

Z.

---

### Post by Xnyper on 2008-02-15
I plan to learn to use makefiles eventually, but this should suffice for my homework.  I appreciate your help, you have answered more questions than i could have hoped for (like why everything I compiled got named a.out).


BTW, that "#pragma once" thing is a neat trick, thanks again.

And Zwack, thanks for lookin' out for me there.  I wouldn't have thought of it initially, but it makes sense that it would be that way--for information hiding purposes (and possibly memory allocation ones?)

---

### Post by hod139 on 2008-02-15
> **Zwack said:**
> The one issue that I was going to mention that hod139 missed was that if the header for circle references something public about circle that requires point then you should probably include point.h in circle.h rather than in circle.cpp.  If it only uses it privately then you should include it in circle.cpp rather than circle.h.

In other words if something uses circle and the public definition of circle includes point then you need to include the definition of point whenever you include the definition of circle to make sure that they have all of the information that they need as it is possible that they don't need to know about point themselves.  The easiest way to do that is to have the header file include other relevant header files... And yes you need some way of making sure that the header file is only really included once.

Z.

I don't fully understand what you are saying (I think I know what you mean though).  If circle.h does not need to access any of point's data, then circle.h should have a pointer to a point, and only include point.h in circle.cpp.  For example:
```

#pragma once
#include <cstddef> // for NULL

class point; // forward declare point class

class circle{
 public:
   circle() : aPoint(NULL) {}
   void circleFunc() const;
 private: 
   point *aPoint;
};
```circle.h

(Cue aks44 telling me I should use an std::auto_ptr here instead of a C style pointer :))

```

#include "circle.h"
#include "point.h"
#include <iostream>

void circle::circleFunc() const{
  std::cout << "In Circle Function\n";
}

```An now, including circle.h does not also make you include point.h, potentially saving compilation time.

---

### Post by Zwack on 2008-02-15
Thanks Hod for putting it a lot more clearly than I did...

Z.

---

### Post by aks44 on 2008-02-15
> **hod139 said:**
> ```
class point; // forward declare point class

class circle{
 public:
   circle() : aPoint(NULL) {}
   void circleFunc() const;
 private: 
   point *aPoint;
};
```

(Cue aks44 telling me I should use an std::auto_ptr here instead of a C style pointer :))

Not necessarily, as long as the "circle" class has a destructor that takes care of cleaning the pointer up, and that it has *no other* member that can throw during construction (which makes "circle" a RAII class of its own). :p

But yeah, std::auto_ptr would be easier to use (less things to think about). ;)

---

