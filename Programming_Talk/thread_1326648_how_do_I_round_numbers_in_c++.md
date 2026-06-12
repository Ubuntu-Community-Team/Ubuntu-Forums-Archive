---
title: "how do I round numbers in c++?"
date: 2009-11-14
forum: Programming Talk
---

### Post by jdunn on 2009-11-14
I have a floating point number I want to round to a certain number of decimal places.

ex:  0.250000000005 needs to round to and print out as 0.25

How do I do this with the standard libraries?

---

### Post by jdunn on 2009-11-14
bump.  this seems like a simple question.  Need an answer in order to do a homework assignment.

---

### Post by Arndt on 2009-11-14
> **jdunn said:**
> bump.  this seems like a simple question.  Need an answer in order to do a homework assignment.

Do you expect an answer in less than half an hour?

I think your number is probably fine - you just want it printed with a convenient number of decimals. So it's not rounding you need but an option to the printing method. Apart from that I actually don't know, since I'm not that good at C++.

---

### Post by movieman on 2009-11-14
Google or look up 'iomanip' in a C++ book; I think you're looking for something like 'setprecision(x)'.

---

### Post by whoop on 2009-11-14
[http://www.cplusplus.com/reference/iostream/manipulators/setprecision/](http://www.cplusplus.com/reference/iostream/manipulators/setprecision/)

---

### Post by dwhitney67 on 2009-11-14
```

#include <iostream>
#include <iomanip>
#include <cmath>

int main()
{
   using namespace std;

   double value = 0.2582345678;

   cout << "value = " << value << endl;
   cout << "value = " << setprecision(2) << value << endl;
}

```

EDIT:  Mathematical way to do it (of course, the code is not bullet proof):
```

#include <iostream>
#include <cmath>

double pround(const double value, const unsigned int decimalPlaces = 2)
{
   if (decimalPlaces == 0)
      return value;

   const double factor = pow(10, decimalPlaces);
   double       tmp    = value * factor + 0.5;

   return (int)tmp / factor;
}

int main()
{
   using namespace std;

   double value = 0.258372;

   cout << "Original value           : " << value << endl;
   cout << "Tenths precision         : " << pround(value, 1) << endl;
   cout << "Hundreths precision      : " << pround(value, 2) << endl;
   cout << "Thousandths precision    : " << pround(value, 3) << endl;
   cout << "Ten-Thousandths precision: " << pround(value, 4) << endl;
}

```

---

### Post by SledgeHammer_999 on 2009-11-14
I think he actually wants to round them first. 0.250000000005 notice the '5' in the end...

---

### Post by slavik on 2009-11-14
rounding floats is a losing game.

---

### Post by dwhitney67 on 2009-11-14
> **SledgeHammer_999 said:**
> I think he actually wants to round them first. 0.250000000005 notice the '5' in the end...
Whatever; the OP is MIA.  Probably cleared his noggin with some fresh air and solved this trivial problem himself.

P.S.  I noticed the '5' at the end of his sample number given by the OP.

P.S. #2  I also drew conclusions about the OP's ability to solve trivial rounding problems using *any* programming language.

---

### Post by TheBuzzSaw on 2009-11-15
> **slavik said:**
> rounding floats is a losing game.

[img]http://i271.photobucket.com/albums/jj155/jamesY2008/clapping.gif[/img]

---

### Post by cariboo on 2009-11-15
it is against forum policy to do your homework for you. This thread is closed.

---

