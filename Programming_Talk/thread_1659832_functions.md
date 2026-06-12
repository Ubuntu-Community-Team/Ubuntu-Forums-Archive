---
title: "functions"
date: 2011-01-04
forum: Programming Talk
---

### Post by Dorian Mayorquin on 2011-01-04
Hi guys, i'm having trouble with this code:

#include<iostream>
#include<cmath>

using namespace std;

int main()

{
    double a = 8;


    cout << "This is tangent of 8\n"<< tan(a)   <<endl;

    return 0;
}

it keeps giving me the wrong result it says that is: -6.79971

---

### Post by Arndt on 2011-01-04
> **Dorian Mayorquin said:**
> Hi guys, i'm having trouble with this code:

#include<iostream>
#include<cmath>

using namespace std;

int main()

{
    double a = 8;


    cout << "This is tangent of 8\n"<< tan(a)   <<endl;

    return 0;
}

it keeps giving me the wrong result it says that is: -6.79971

It's probably correct. The argument is in radians, not degrees.

---

### Post by Lootbox on 2011-01-04
Arndt is correct. A good place to look these types of things up is at [http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/). The entry for the tan function ([**here**](http://www.cplusplus.com/reference/clibrary/cmath/tan/)) explains what type of parameter it expects.

---

### Post by WRDN on 2011-01-04
tan(8.0) is equal to -6.79971, as the parameter provided is radians, as Arndt noted.

If you want to convert between them:

Radians = Degrees * (PI/180)
Degrees = Radians * (180/PI)
PI = 3.14159265

---

