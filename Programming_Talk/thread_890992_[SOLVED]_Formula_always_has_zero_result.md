---
title: "[SOLVED] Formula always has zero result"
date: 2008-08-15
forum: Programming Talk
---

### Post by speedkreature on 2008-08-15
First, let me preface this by saying thank you to all who respond.  Second, I haven't touched C++ since I started teaching myself C and just ran into it back in '94..

Here's the problem code.

```
#define max_val ((2^(sizeof(int)*8))/64)
```

I'm expecting a value of around 6.7 Million, but I'm getting zero.  Even ```
 cout << (2^32);
```
prints 0 to the screen.  Not sure what gives.

---

### Post by slavik on 2008-08-15
are you on a 32 bit machine? if so, it makes perfect sense why 2^32 would be 0. hint: start counting at 0.

---

### Post by hod139 on 2008-08-15
> **speedkreature said:**
> <snip>```
 cout << (2^32);
```prints 0 to the screen.  Not sure what gives.

In C (and C++) 2^32 is performing a bitwise exclusive or (XOR) between 2 and 32.  
(000010 XOR 100000 = 000000) 

It is not raising 2 to the 32 power.  If you want to raise 2 to the 32 power, you have to use the pow function.  As slavik noted though, do not try to do the exponentiation with ints (pow won't let you). If you try to do this with int precision, a 32 bit machine can only store a maximum value of to 2^32-1, so 2^32 will loop pass infinity and go back to 0.

---

### Post by WW on 2008-08-15
As hod139 explained, **^** is not the exponentiation operator in C/C++.

Because the base is 2, you can use the shift operator instead; that is, to compute 2^k, you can use 1 << k (assuming k >= 0).  Also, in your formula, you divide by 64 which is 2^6; you can get the same effect by subtracting 6 from the shift amount.  That is, (2^k)/64 = 2^(k-6).  So, this should work:
```

#define max_val ( 1 << (sizeof(int)*8-6) )

```

For example,
```

$ cat max_val_test.cpp

#include <iostream>

#define max_val ( 1 << (sizeof(int)*8-6) )

using namespace std;


int main()
    {
    cout << "int is " << sizeof(int) << " bytes.\n";
    cout << "max_val is " << max_val << endl;
    return 0;
    }

$ g++ -Wall max_val_test.cpp -o max_val_test
$ ./max_val_test 
int is 4 bytes.
max_val is 67108864
$ 

```

---

### Post by slavik on 2008-08-15
heh, I forgot that ... :(

---

### Post by speedkreature on 2008-08-16
Wow...I kind of figured is was a simple as that.  Guess I need to start from the basics again.
Thanks for the expedient replies.  

I saw another post regarding pow before posting this one however I got errors when compiling...guess that's related to the integer problem.

Now I'm off to find some interactive web-based primers on C++.

You guys rock!

---

### Post by British0zzy on 2008-08-16
Check out the header file, limits.h. It will contain all the values pertaining to the maximum or minimum of an int or a long or any other number (except floats).
float.h will contain the limits for floating point numbers.

---

### Post by dwhitney67 on 2008-08-16
Here's an example, in C, of the pow() function:
[PHP]#include <math.h>       // for pow()
#include <stdio.h>

int main()
{
  const double value = 4.0;
  const double power = 2.0;

  printf( "4^2 = %f\n", pow( value, power ) );

  return 0;
}[/PHP]
To correctly link the program, you need to include the math library:
```
$ gcc pow_ex.c -lm
```

P.S.  If coding in C++, replace the <math.h> with <cmath>.  The linking of the math library is not required.

---

