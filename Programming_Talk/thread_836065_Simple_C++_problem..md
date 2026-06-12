---
title: "Simple C++ problem."
date: 2008-06-21
forum: Programming Talk
---

### Post by MdaG on 2008-06-21
Hi,

I'm trying to write a function for finding recurring fractions of an arbitrary rational number, but I get a strange error probably related to floating point precision, but I don't understand it at all.

Here's the code:
```
void getContinuedFraction(double number, vector<int>& continuedFractions) {
   const double eps = 1e-9;
   double delta = 1.0;
   int integerPart = 0;
   int i = 1, max = 5;
   while(fabs(number) > eps) {
      cout << i << " lastnumber  = " << number << endl;
      integerPart = static_cast<int>(number);
      number = number - static_cast<double>(integerPart);
      continuedFractions.push_back(integerPart);
      cout << i << " integerPart = " <<  integerPart << endl;
      cout << i << " number      = " <<  number << endl;
      number = 1.0 / number;
      cout << i << " 1/number    = " <<  number << endl << endl;;
      i++;
      if(i == max){return;}
   }
}
```
Calling this function with 3.245 and an arbitrary empty vector gives the following output:
```
1 lastnumber  = 3.245
1 integerPart = 3
1 number      = 0.245
1 1/number    = 4.08163

2 lastnumber  = 4.08163
2 integerPart = 4
2 number      = 0.0816327
2 1/number    = 12.25

3 lastnumber  = 12.25
3 integerPart = 12
3 number      = 0.25
3 1/number    = 4

4 lastnumber  = 4
4 integerPart = 3 <---- Why isn't this equal to four (4) !?
4 number      = 1
4 1/number    = 1
```
I've marked the line where I don't understand what's happening.
I'm writing it in Kate and I've tried getting access to a debugger through KDevelop, but I don't know how to set it up. Compiling won't work unless I configure something so I gave up on that idea for now.

---

### Post by lisati on 2008-06-21
I'm not overly conversant with C++, but would suspect that there might be rounding going on.

---

### Post by canadiandude007 on 2008-06-21
Hello,

You've come across the basic 'rounding off error'.

Take a closer look at the real output and this should shed some light on why you get a 3 instead of a 4.

/*
Hello, please enter a number: 
3.245
1 lastnumber  = 3.245
1 integerPart = 3
1 number      = 0.245
1 1/number    = 4.08163 <- 4.081632653

2 lastnumber  = 4.08163
2 integerPart = 4
2 number      = 0.0816327 <- 0.081632653
2 1/number    = 12.25 <- 12.250000009

3 lastnumber  = 12.25 <- 12.250000009
3 integerPart = 12
3 number      = 0.25 <- 0.250000009
3 1/number    = 4 <- 3.999999856

4 lastnumber  = 4 <- 3.999999856
4 integerPart = 3
4 number      = 1
4 1/number    = 1
*/

So, the integerPart will still grab the static_cast<int> 3 value instead of a 4.

Cheers!

---

### Post by canadiandude007 on 2008-06-21
Presuming you are using ...
```

#include <cmath>
using namespace std;

```

Then change this line to ...

```

      integerPart = static_cast<int>(round(number));

```

Your about will then be something like this ...

4 lastnumber  = 4
4 integerPart = 4
4 number      = -4.03588e-12
4 1/number    = -2.47777e+11


Hope that helps!

---

### Post by MdaG on 2008-06-21
Thanks!
Yes, it certainly shed the needed light on this. However I should use something more foolproof than rounding off the number before truncating it to an integer as the true fraction could very well lie closer to the upper integer. e.g.) When the starting number is 3.9.

---

