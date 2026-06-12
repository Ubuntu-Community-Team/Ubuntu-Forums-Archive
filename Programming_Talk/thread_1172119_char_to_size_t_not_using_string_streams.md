---
title: "char* to size_t not using string streams"
date: 2009-05-28
forum: Programming Talk
---

### Post by monkeyking on 2009-05-28
Hi does anyone know how to make a char* to type size_t,

stringstreams are to slow.

Thanks in advance.

---

### Post by dwhitney67 on 2009-05-28
> **monkeyking said:**
> Hi does anyone know how to make a char* to type size_t,

stringstreams are to slow.

Thanks in advance.

Your question makes no sense, and your comment comes in a close second place.

A char* is a pointer to a series of one or more bytes, typically (but not always) ending in a null-character.  This series of bytes, typically (but not always) represents a string.

A size_t is synonymous with an unsigned int, and is used to represent a dimension of an object, whether it be an STL string, or the size of a vector, or some other object.

So, comparing char* and size_t is like comparing apples and oranges.  Forget about trying to convert from one to the other.

Wrt to your second comment, that stringstreams are slow... compared to what?

---

### Post by monkeyking on 2009-05-28
Hi, sorry for not being clearly enough

If i got an a very large int, hiding in a char* like
[PHP]
const char* val = "1111111111111111111111111111";
[/PHP]

This is to large for any int to represent,
so I'd like to store it as a long int og preferely as a size_t.

I can do atol, which will be a long int.
But I would prefer size_t.

Thanks for you response.

---

### Post by dwhitney67 on 2009-05-28
In lieu of the size_t, declare an unsigned long long.  However, if you go this route, then your code is no longer ISO C++ compliant.

A size_t, along with an unsigned long int, occupy 4-bytes.  For a large number, such as the one in your example, you would need a (unsigned) long long, which is 8-bytes in size.

P.S.  atol() works on values that are 4-bytes in size, thus your value would exceed that limitation.

P.S.S.  Why would you need such a large number anyhow?

---

### Post by monkeyking on 2009-05-28
Hi my huge values are indeed dimensions of something,
I'm just reading them as char* from a file.

A size_t is a long unsigned int, that should be 8 bytes (in gcc atleast right?)

as goes with the slowness of the streams see this thread [http://ubuntuforums.org/showthread.php?t=1158564](http://ubuntuforums.org/showthread.php?t=1158564) .


I'm reading extremely large file containing some dna genetic stuff.
And many of these files large files.

Thanks for your response.

---

### Post by johnl on 2009-05-28
Hi, 

depending on the magnitude of your values you may need to use an external 'bignum' library like gmp.  This lets you handle arbitrarily large data.  Install libgmp3-dev and link with -lgmp (to use C++ classes as below, also use -lgmpxx)

```

#include <iostream>
#include <gmpxx.h> // gmp.h for C interface


int main(int argc, char* argv[])
{
    mpz_class a, b;

    a = 12351252;
    b = "35781257195713905";

    std::cout << a << '+' << b << '=' << (a+b) << std::endl;

    return 0;
}

```

---

