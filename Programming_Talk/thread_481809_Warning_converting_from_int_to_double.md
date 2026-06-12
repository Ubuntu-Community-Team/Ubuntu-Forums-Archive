---
title: "Warning: converting from int to double"
date: 2007-06-22
forum: Programming Talk
---

### Post by OhioYJ on 2007-06-22
Warning: converting from int to double

Ok so I have that warning. The program works fine, is it really anything to worry about? 

I use several double variables to create an int. I did it this way to get rid of the decimals in the result. I tried static cast and set precision, but neither worked quite right.

---

### Post by WW on 2007-06-22
The C++ way to convert from a double to an int is with static_cast:
```

int m;
double x;

m = static_cast<int>(x);

```
But that is not the only way:
```

#include <iostream>

using namespace std;

int main()
    {
    int i, j, k, m;
    double x;

    x = 4.567;

    i = x;        // OK, but results in a warning.
    j = (int) x;  // C-style cast.
    k = int(x);   // Initialize an integer, and copy it to k
    m = static_cast<int>(x); // C++ cast (preferred by C++ aficionados)

    cout << "i=" << i << endl;
    cout << "j=" << j << endl;
    cout << "k=" << k << endl;
    cout << "m=" << m << endl;

    return 0;
    }

```

---

### Post by OhioYJ on 2007-06-22
Thanks, thats what I needed. I had it backwards, solves that issue.

> int m;
double x;

m = static_cast<int>(x);

---

### Post by teki on 2009-11-24
Hello!

I tried using static_cast but I notices a problem. Here's a simple code I wrote to investigate it and the result that I get.

```

#include <iostream>

using namespace std;

int main(){

  double n1 = .04;
  double n2 = .045;
  double n3 = .005;

  double n4 = (n2-n1)/n3;
  int n =static_cast<int>(n4);
  cout << n4 << " = " << n << endl;

  return 0;

}

```Output:
> 1 = 0I think the problem is self-explanatory ;)
Any ideas why I get this result and how to get that 1 actually equals 1?

Cheers!

---

### Post by Zugzwang on 2009-11-24
> **teki said:**
> 
Any ideas why I get this result and how to get that 1 actually equals 1?


This is due to rounding errors. The point here is that "double" does not contain precise floating point numbers but rather approximate ones (see the wikipedia article on floating point numbers: [http://en.wikipedia.org/wiki/IEEE_754-2008](http://en.wikipedia.org/wiki/IEEE_754-2008)). When doing a static cast, you always perform rounding to the next *lower* integer, which is 0 for 0.999999999991545 (or something like that). The fact that std::cout << n4;" gives "1" is due to the fact that the iostream function perform rounding in a different way.

Here is some mantra that every user of floating point numbers should remember in one form or the other: **Never compare a floating point number with something else for equality. Rounding errors will make such an operation likely to fail.**

Hope that helps.

---

### Post by teki on 2009-11-24
I understand why the problem occurs now. Thanks!
But I still don't know how to get 1 to be equal to 1. I need somehow to convert double to int and to get these numbers to match.

---

### Post by MindSz on 2009-11-24
Easiest way I know to convert double (or float) to int:

```
#include <stdio.h>

int main(){

  double n1 = .04;
  double n2 = .045;
  double n3 = .005;

  double n4 = (n2-n1)/n3;
  int n = (int)(n4+0.5);

  printf("%f = %d\n",n4,n);


  return 0;
}
```

Just add 0.5 to the float.

---

### Post by teki on 2009-11-24
Yes, that's what I did, and it works, but I'm not to happy with that solution. Somehow, I'm afraid there could be a case in which this makes a mess.

We'll see...

Thanks!

---

### Post by teki on 2009-11-24
> **MindSz said:**
> Just add 0.5 to the float.

Yes, that's what I did, and it works, but I'm not to happy with that solution. Somehow, I'm afraid there could be a case in which this makes a mess.

We'll see...

Thanks!

---

### Post by Arndt on 2009-11-24
> **teki said:**
> Yes, that's what I did, and it works, but I'm not to happy with that solution. Somehow, I'm afraid there could be a case in which this makes a mess.

We'll see...

Thanks!

Yes, all numbers for which the result is negative.

---

