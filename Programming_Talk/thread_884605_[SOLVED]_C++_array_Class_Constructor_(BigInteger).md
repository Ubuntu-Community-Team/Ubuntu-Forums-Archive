---
title: "[SOLVED] C++ array Class Constructor (BigInteger)"
date: 2008-08-09
forum: Programming Talk
---

### Post by WitchCraft on 2008-08-09
Hi, the following problem:

I am writing a C++ class for the whirlpool hash algorithm.

Now I got into a problem:
I need to declare arrays that look like this:

```

static const u64 someBox[] =
{
0x0000000000000000LL,
0x1823c6e887b8014fLL,
0x36a6d2f5796f9152LL,
0x60bc9b8ea30c7b35LL,
0x1de0d7c22e4bfe57LL,
0x157737e59ff04adaLL,
0x58c9290ab1a06b85LL,
0xbd5d10f4cb3e0567LL,
0xe427418ba77d95d8LL,
0xfbee7c66dd17479eLL,
0xca2dbf07ad5a8333LL
};

```
Now data-type u64 doesn't exist in C++.
But __int64 does:
error C2440: 'initializing' : cannot convert from '__int64' to 'const BigInteger'

I have a BigInteger Class, and I can initialize numbers to BigInteger.

However I don't know how to initialize an array like this.

until now i do:
```

std::string strSomeValue = "ca2dbf07ad5a8333"
BigInteger aNumber = StringToBigInt(strSomeValue )

```

How can I write a constructor to initialize the entire array?
Best would be if I could write

```

static const BigInteger someBox[] =
{
0x0000000000000000LL,
0x1823c6e887b8014fLL,
0x36a6d2f5796f9152LL,
0x60bc9b8ea30c7b35LL,
0x1de0d7c22e4bfe57LL,
0x157737e59ff04adaLL,
0x58c9290ab1a06b85LL,
0xbd5d10f4cb3e0567LL,
0xe427418ba77d95d8LL,
0xfbee7c66dd17479eLL,
0xca2dbf07ad5a8333LL
};

```

I don't care if I have to put every number between quotes, as I can do this with sed if necessary.
But I would prefer initializing without quotes.

---

### Post by catchmeifyoutry on 2008-08-09
> **WitchCraft said:**
> Hi, the following problem:


I don't care if I have to put every number between quotes, as I can do this with sed if necessary.
But I would prefer initializing without quotes.

So can't you just make it an array of strings, and use a loop to fill an array of BigIntegers by parsing each string?
Otherwise, if your BigInteger class has a const char * constructer then you could do something like this:

[PHP]
#include <iostream>
#include <string>

using namespace std;

class A
{ 
   string x;

public:
    A (const char * _x) : x (_x)
    { }

    void foo() { 
        cout << "x = " << x << endl;
    }

};


int main()
{ 
    A a[] = {
        "hello",
        "foobar",
        "world"
    };

    // print "foobar"
    a[1].foo();

    return 0;
}

[/PHP]

---

### Post by WitchCraft on 2008-08-20
bump. Anybody has a better idea?

---

### Post by dwhitney67 on 2008-08-20
> **WitchCraft said:**
> bump. Anybody has a better idea?

What is that you want?  It is it a typedef for BigInteger?  Maybe
[PHP]#include <stdint.h>
typedef uint64_t BigInteger;[/PHP]

---

### Post by kpatz on 2008-08-20
Code a constructor that accepts a 64-bit integer (long long, or whatever your compiler uses) and stores it in your class.

If you want to initialize your big numbers using strings, code a constructor that accepts a string and calls StringToBigInt (or atoll or strtoll in GNU C++).

When you initialize an array of classes, the compiler will call the constructor that matches the data type being passed in the array.  You don't have to do any special coding in your class to initialize an array of your class.

Is BigInteger a class you created, or out of some library?  If you created it (or have the source code and can change it), add the constructors you need.  If it's from a library, create a class derived from BigInteger and add your constructors.

Here's an example:
[php]
#include <iostream>
using namespace std;

// Here's a "BigInteger" class that has constructors for either a big integer
// or a string containing a big integer.
class BigInteger
{
 public:
  long long num;
  BigInteger() { num = 0; }
  BigInteger(const long long x) { num = x; };
  BigInteger(const char *in) { num = atoll(in); };
};

main()
{
// Look at this, we can even pass mixed types to the array,
// as long as we have constructors that accept the types we're passing!
  BigInteger a[] = { 5, "6", 8 };
  for (int i = 0; i < 3; i++)
    cout << "a[" << i << "] is " << a[i].num << endl;
}
[/php]

---

### Post by WitchCraft on 2008-08-22
> **kpatz said:**
> 
If it's from a library, create a class derived from BigInteger and add your constructors.


Ah, a simple but most useful tip. I've written it myself, though.

So, if the values I initialize are larger than a 64 Bit integer, that means I need to include every number in quotes, wasting a lot of memory space by loading many char* or strings?

Is there really no other way?
If yes, then the C++ preprocessor is really weak...

---

### Post by mujambee on 2008-08-22
If you have variable length numbers you can use a variable length initializer:


```
class BigInteger
{
 public:
    BigInteger( unsigned int val, ... )
};


BigInteger a[] = { 3, ( 3, 4 ), ( 3, 4, 5 ) };

```

Or, for your example:

```
static const BigInteger someBox[] =
{
(0x00000000,0x00000000),
(0x1823c6e8,0x87b8014f),
(0x36a6d2f5,0x796f9152),
(0x60bc9b8e,0xa30c7b35),
(0x1de0d7c2,0x2e4bfe57),
(0x157737e5,0x9ff04ada),
(0x58c9290a,0xb1a06b85),
(0xbd5d10f4,0xcb3e0567),
(0xe427418b,0xa77d95d8),
(0xfbee7c66,0xdd17479e),
(0xca2dbf07,0xad5a8333)
};
```

Drawback is that you have to split your numbers in 32 bit chunks.

---

### Post by dwhitney67 on 2008-08-22
> **WitchCraft said:**
> Ah, a simple but most useful tip. I've written it myself, though.

So, if the values I initialize are larger than a 64 Bit integer, that means I need to include every number in quotes, wasting a lot of memory space by loading many char* or strings?

Is there really no other way?
If yes, then the C++ preprocessor is really weak...
I've been reading through this thread, and still to this moment, I haven't a clue what your requirement is.  Can you please re-elaborate what is it that you require?

In your OP, you stated that u64 does not exist.  That is correct.  Your choice is to use uint64_t when coding for Linux.  This is defined in stdint.h.

As for C/C++, I am not aware of any native storage that handles numbers greater than 64-bits.  I think the Boost C++ libraries are attempting to provide a BigInt(eger) library object similar to that which is available in Java, but I do not believe it has been released yet.

If you are writing code that will be ported to Windoze, then consider something like this:
[PHP]#ifdef WIN32
    typedef __int64 BigInt;
#else
    typedef int64_t BigInt;
#endif[/PHP]
Bear in mind that with a "signed" 64-bit storage space (as shown above), you really only get to use the first 63 bits, with the last bit reserved for the sign bit.  If it is unsigned values that you need, then replace the int64's with uint64's.

Also bear in mind if you compile with the -pedantic GCC option, that utilizing "long long" (or LL) will generate a compiler warning.

Anyhow, please be a little more specific as to what your requirements are.  I'm confused as to whether you need to store numbers that are larger than will fit in a 64-bit value.

---

### Post by kpatz on 2008-08-22
If you need to pass numbers that are too big for 64-bit integers to your class, you'll have to either use strings or split the numbers up somehow.  There are no integer constants in C++ larger than a 64-bit int.

If you're concerned about using string literals due to storage space, you could use integer constants for the values that fit into them, and strings for those that don't.  By having 2 constructors in your class, one that accepts 64-bit int and one that accepts a string, your class will handle it nicely.  Or split the numbers up somehow, but then you'll have to translate them.

---

### Post by mujambee on 2008-08-22
> **kpatz said:**
> If you need to pass numbers that are too big for 64-bit integers to your class, you'll have to either use strings or split the numbers up somehow.  There are no integer constants in C++ larger than a 64-bit int.

If you're concerned about using string literals due to storage space, you could use integer constants for the values that fit into them, and strings for those that don't.  By having 2 constructors in your class, one that accepts 64-bit int and one that accepts a string, your class will handle it nicely.  Or split the numbers up somehow, but then you'll have to translate them.

That was exactly what I was trying to address with my approach...

---

### Post by WitchCraft on 2008-08-22
> **mujambee said:**
> If you have variable length numbers you can use a variable length initializer:


```
class BigInteger
{
 public:
    BigInteger( unsigned int val, ... )
};


BigInteger a[] = { 3, ( 3, 4 ), ( 3, 4, 5 ) };

```

Or, for your example:

```
static const BigInteger someBox[] =
{
(0x00000000,0x00000000),
(0x1823c6e8,0x87b8014f),
(0x36a6d2f5,0x796f9152),
(0x60bc9b8e,0xa30c7b35),
(0x1de0d7c2,0x2e4bfe57),
(0x157737e5,0x9ff04ada),
(0x58c9290a,0xb1a06b85),
(0xbd5d10f4,0xcb3e0567),
(0xe427418b,0xa77d95d8),
(0xfbee7c66,0xdd17479e),
(0xca2dbf07,0xad5a8333)
};
```

Drawback is that you have to split your numbers in 32 bit chunks.

Aaaaah, soooo simple, why didn't I got on the idea...
I like the concept.

> 
If you are writing code that will be ported to Windoze, then consider something like this:
[PHP]#ifdef WIN32
    typedef __int64 BigInt;
#else
    typedef int64_t BigInt;
#endif[/PHP]

Actually, I've already done this, and it compiles well on MinGW, but my problem is that it doesn't  compile with the Microsoft Compiler.

> **kpatz said:**
> If you need to pass numbers that are too big for 64-bit integers to your class, you'll have to either use strings or split the numbers up somehow.  There are no integer constants in C++ larger than a 64-bit int.

If you're concerned about using string literals due to storage space, you could use integer constants for the values that fit into them, and strings for those that don't.  By having 2 constructors in your class, one that accepts 64-bit int and one that accepts a string, your class will handle it nicely.  Or split the numbers up somehow, but then you'll have to translate them.

I'll simply overload the constructor to support char*, string, int, long, char, MYINT64, splitted, and fully remove long long.

---

