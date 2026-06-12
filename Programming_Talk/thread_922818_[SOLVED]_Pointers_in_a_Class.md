---
title: "[SOLVED] Pointers in a Class"
date: 2008-09-17
forum: Programming Talk
---

### Post by kjohansen on 2008-09-17
I am playing with pointers and I found something that I do not understand.

I have the header file:
```

#ifndef DATE_H_INCLUDED
#define DATE_H_INCLUDED
class Date{
  int p;
  int a;
  public:
    int *pp;
    int test();
    void test2();
};


#endif // DATE_H_INCLUDED

```

and the the code file
```

#include <iostream>
#include "Date.h"

using namespace std;

int Date::test(){
    return 3000;
}

void Date::test2(){
    *pp=3039303;
    cout<<*pp;
}

```

And I get a segmentation fault.

If i change the test2 function to

```

void Date::test2(){
    int * ff;
    *ff=3039303;
    cout<<*ff;
}

```

it works.

Why cant I access the pointer in the class? I can access the other variables fine.

---

### Post by rbprogrammer on 2008-09-17
The simple answer for me to say would be because you have a pointer (obviously), but then you try to dereference it.  Before you dereference it, you must have it assigned to a "valid" address with (in this case you are using c++) the "new" operator.

Try this:

Date.h
```

#ifndef DATE_H_INCLUDED
#define DATE_H_INCLUDED
class Date
{
    int p;
    int a;
public:
    int *pp;
    int test();
    void test2();
};
#endif // DATE_H_INCLUDED

```
Date.c
```

#include <iostream>
#include "Date.h"
using namespace std;

int Date::test()
{
    return 3000;
}

void Date::test2()
{
    pp = new int;
    *pp = 3039303;
    cout << *pp;
}

```

As far as that error where you changed the code inside Date::test2(),  I would just say that might have been a glitch, or for something that I cannot think of right now.

Try to see if that code will work for you.  I am on the old antiquited Solaris machines in one of the buildings on campus over here, so I won't be able to test it.  Keep us informed, because this is part of the learning process.  God knows all of us made a ton of simple mistakes whe it comes to pointers in C and C++.

---

