---
title: "default values in array initialization c++"
date: 2007-11-23
forum: Programming Talk
---

### Post by monkeyking on 2007-11-23
Hi,
I'm having deficilties finding an answer to the following question.
Or more correctly, I'm getting alot of different answers.


When I initialize an array in the following way
```

double *my_array = new doubl[3]

```

What are the default values, (apperantly it's zero), but can I be sure of this value, and will it be the same on different platforms and different compilers.

thanks in advance

---

### Post by LaRoza on 2007-11-23
The values of the array will be random.

You can use memset() to zero the array if you want.

---

### Post by aks44 on 2007-11-23
For scalars, the default value is: *whatever value was there before* (aka. *uninitialized* values).

For objects, the compiler will instantiate them using the default constructor of the class.


Arrays don't give you much control over their initialization, which is yet *another* reason to prefer vectors.

---

### Post by monkeyking on 2007-11-23
Thanks,

---

### Post by dwhitney67 on 2007-11-23
yep, the previous post are correct.

However, if you know your array will only contain 3 (or some other fixed sized) items, then you can initialize the array using memset() or:

```
double myArray[ 3 ] = { 0.0 };
```

---

### Post by aks44 on 2007-11-23
> **dwhitney67 said:**
> ```
double myArray[ 3 ] = { 0.0 };
```

You meant

```
double myArray[ 3 ] = { 0.0, 0.0, 0.0 };
```right?

Otherwise only the first item will be initialized.

---

### Post by dwhitney67 on 2007-11-23
No, I was correct.  Run a test program to verify.  I've been doing initialization like I posted for years... never once a problem.

---

### Post by aks44 on 2007-11-23
On Feisty, g++ 4.1.2 :

```
#include <iostream>

int main()
{
  double t[3] = { 3.0 };
  for (int i = 0; i < 3; ++i)
    std::cout << i << " = " << t[i] << std::endl;
  return 0;
}
```

```
$ g++ -o test test.cpp
$ ./test
0 = 3
1 = 0
2 = 0
$
```


FWIW, I was pretty surprised by your post so I tested it before even replying to it... :)
EDIT: also, not using any initializer gives me a zero'ed out array anyway.

---

### Post by dwhitney67 on 2007-11-23
Odd, this is the output I get without the initialization:
```
val 0 = 5.75448e-316
val 1 = 4.85783e-270
val 2 = 4.91912e-275
```

When I initialize using the statement I provided:
```
val 0 = 0
val 1 = 0
val 2 = 0
```


Here's my program... which is very similar to yours:

```
#include <iostream>

using namespace std;

int main()
{
  double myArray[ 3 ] = { 0.0 };

  for ( int i = 0; i < 3; ++i )
  {
    cout << "val " << i << " = " << myArray[i] << endl;
  }
}
```

P.S.  I am using GCC 4.1.2 on Fedora.  I never use Ubuntu for development purposes.

P.S.S.  I ran another test, with the initialization set to { 3.0 } like your test program; I got the same results as you did.  I guess I never thought of that.  Generally I initialize my arrays to zero (whether they be doubles, chars, or unsigned chars) and it has always worked for my needs.  If I needed to initialize to a non-zero value, then I would use memset().

---

### Post by aks44 on 2007-11-23
> **dwhitney67 said:**
> Odd, this is the output I get without the initialization:

I tested the "uninitialized" version again, and finally got non-zero values (after a few tries). I guess those zeros just happened to lie where the OS had put the stack, but it's still surprising (well, quite unlikely anyway) that I got this result several times. Not the first time I notice zero-initialized local variables on my Ubuntu though. :confused:

---

### Post by geirha on 2007-11-24
On consequtive runs of the same program, it's likely it gets the same part of memory each time, which would explain why you got 0s several times. 

Compilers may allow you to initialize all variables automatically with some configuration option, and some compilers even do this by default (g++ does not do this by default). One reason for not initializing variables automatically, is that sometimes you don't need to set a start value, and you lose some cpu cycles setting these values which are never going to be used anyway.

I believe the d language initializes variables by default, but provides an extra keyword to specify that you don't want the variable initialized.

---

### Post by TreeFinger on 2007-11-24
When an array is partially initialized, the remaining uninitialized elements are automatically assigned to 0.

---

### Post by dwhitney67 on 2007-11-24
Obviously.

---

