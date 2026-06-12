---
title: "outputting a function in color"
date: 2008-04-27
forum: Programming Talk
---

### Post by the_real_fourthdimension on 2008-04-27
Hi

I'm creating a "screensaver" of sorts.  I have this code and I want to output the random function in a color.
```

#include <cstdlib>
#include <iostream>


using namespace std;

int main (int argc, char** argv)
{
static const int MAX = 2;

while (1)
   {
   cout<< rand() % MAX;  //I want to change the color of this line

   }
return 0;
}

```

I'd imagine that I'd have to use hex values for the colors, but how would I apply the color to the function I want to output?
Thanks.

---

### Post by dwhitney67 on 2008-04-27
Good luck, because AFAIK, there is no way to do what you want using the std::cout stream.  The std::hex manipulator is merely for printing integer values as a hexidecimal number.  By default, std::dec is enabled.

Btw, you should seed the random number generator before calling rand().  For example:
[PHP]srand( time(0) );[/PHP]

---

### Post by the_real_fourthdimension on 2008-04-27
Ah, I was afraid of that...
Thanks for your reply.
What does seeding do?

---

### Post by dwhitney67 on 2008-04-27
From the man-page for rand() and srand():
```
...
The  srand()  function  sets  its argument as the seed for a new sequence of pseudo-random
integers to be returned by rand().  These sequences are repeatable by calling srand() with
the same seed value.

If  no seed value is provided, the rand() function is automatically seeded with a value of
1.
...
```
The time() function provides a sufficiently large seed value, although if you wanted, perhaps the maximum-sized integer (std::numeric_limits<unsigned int>::max()) would also suffice.

---

