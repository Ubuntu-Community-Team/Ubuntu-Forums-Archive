---
title: "[SOLVED] C++ Mutiple File Project Problem"
date: 2008-09-01
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-09-01
I am working on a multiple file c++ project (just is case you didn't know) and I successfully create a problem.

I have two .h files referring to each other with includes (see bottom for source) the .h files are shielded (see bottom) and when I try compile either file i get this error
```

aidan@aidan:~/Program/C++/C2D$ ls *.h
Base.h  Collsion.h  Event.h  Group.h  Mechanic.h  Point.h  Shape.h  Vector2.h
aidan@aidan:~/Program/C++/C2D$ g++ Vector2.h 
Point.h:22: error: expected ‘,’ or ‘...’ before ‘&’ token
Point.h:22: error: ISO C++ forbids declaration of ‘Vector2’ with no type
Point.h: In constructor ‘Point::Point(int)’:
Point.h:23: error: ‘v’ was not declared in this scope
aidan@aidan:~/Program/C++/C2D$ g++ Point.h 
Vector2.h:22: error: expected ‘,’ or ‘...’ before ‘&’ token
Vector2.h:22: error: ISO C++ forbids declaration of ‘Point’ with no type
Vector2.h: In constructor ‘Vector2::Vector2(int)’:
Vector2.h:23: error: ‘v’ was not declared in this scope
aidan@aidan:~/Program/C++/C2D$ 

```

Here is the include and shielding

Vector2
[PHP]#ifndef VECTOR2_H
#define VECTOR2_H

#include "Base.h"
#include "Point.h"
#include <cmath>

...
...

#endif[/PHP]

Point
[PHP]#ifndef POINT_H
#define POINT_H

#include "Base.h"
#include "Vector2.h"
#include <cmath>

...
...

#endif[/PHP]

---

### Post by monkeyking on 2008-09-01
You should redesign you program,
either make them independant from oneanother,
and then make a third file that encapsultes the sum of them,
or just put everything into one file.

I don't think there is some easy solution, like shielding.
If you can't atleast compile one of them.

good luck

---

### Post by heikaman on 2008-09-01
Well... **monkeyKing** is right this situation does indicate a poor design.

However there's an easy solution which is **forward declarations** of each class.

Vector2
[PHP]
class Point;
[/PHP]

Point
[PHP]
class Vector2;
[/PHP]

This will make g++ stop complaining but you will only be allowed to declare pointers to the classes as they will be seen by the compiler as incomplete types.

---

### Post by monkeyking on 2008-09-02
> **heikaman said:**
> 
...
However there's an easy solution which is **forward declarations** of each class.
...

I've never heard about that, might come in handy some day.

---

### Post by dribeas on 2008-09-02
> **heikaman said:**
> However there's an easy solution which is **forward declarations** of each class.

This will make g++ stop complaining but you will only be allowed to declare pointers to the classes as they will be seen by the compiler as incomplete types.

+1
It is not only a solution, but should be common place. In most cases .h files should (if they can: see limitations above) only forward declare external classes. Then .cpp files will include all required headers.

Note that this will also speed up compilation times, as the inclusion of a header does not force you to include all referred types' headers (as long as they are used only as pointers / references / function parameters).

---

### Post by Mr.Macdonald on 2008-09-02
I have a better idea, I will use inheritance because a Point and a Vector are about the same

---

