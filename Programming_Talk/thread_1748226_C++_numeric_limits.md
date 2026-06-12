---
title: "C++: numeric_limits"
date: 2011-05-03
forum: Programming Talk
---

### Post by erotavlas on 2011-05-03
Hello,

How can I find the overflow of the basic arithmetic types using standard C++?

For instance, if two unsigned long int are multiplied together, test whether or not the result is too large to fit in a long unsigned int?

For example

```
#include <limits>

unsigned long a;
unsigned long b;

if (a*b > std::numeric_limit<unsigned long>::max())
    c = std::numeric_limit<unsigned long>::max();
else
    c = a*b;

```


Thank you.

---

### Post by PaulM1985 on 2011-05-03
You could check the multiplier.

If you have a * b must be less than max_number, you could find max_b using max_number / a.  If max_b is less than b, then the number would be greater than the data type could store.

Paul

---

### Post by Arndt on 2011-05-03
> **PaulM1985 said:**
> You could check the multiplier.

If you have a * b must be less than max_number, you could find max_b using max_number / a.  If max_b is less than b, then the number would be greater than the data type could store.

Paul

Another way is to do the multiplication with full precision, expressing the factors as P*a1+a2 and P*b1+b2, where P has half as many bits as the type of the factors.

---

### Post by erotavlas on 2011-05-04
> **Arndt said:**
> Another way is to do the multiplication with full precision, expressing the factors as P*a1+a2 and P*b1+b2, where P has half as many bits as the type of the factors.

I'm sorry but I have not understood your method...

---

### Post by dwhitney67 on 2011-05-04
> **erotavlas said:**
> I'm sorry but I have not understood your method...

I Googled for "C++ detect overflow", and amongst the many results, here's the first:  [http://stackoverflow.com/questions/199333/best-way-to-detect-integer-overflow-in-c-c](http://stackoverflow.com/questions/199333/best-way-to-detect-integer-overflow-in-c-c)

---

### Post by Arndt on 2011-05-04
> **erotavlas said:**
> I'm sorry but I have not understood your method...

No, sorry, I wasn't detailed enough. The idea is to break down the numbers into smaller units, where you don't get overflow, and then do a combined shifting and addition, where it is easy to check for overflow. I only wanted to convey the idea, you can probably work out the details.

We do the same thing when we multiply numbers by hand: 13 = 1*10+3, 87 = 8*10+7. 13*87 = 1*8*10*10 + 1*7*10 + 3*8*10 + 3*7.

---

