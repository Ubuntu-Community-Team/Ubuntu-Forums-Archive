---
title: "Packing structures in C++"
date: 2009-08-05
forum: Programming Talk
---

### Post by Volt9000 on 2009-08-05
I have a struct in one of my classes that I need packed. Problem is, I'm not sure which notation to use.

I've seen two ways of doing this:

#pragma pack

__attribute__ ((packed))

Which should I be using, or does it even matter?

---

### Post by lensman3 on 2009-08-06
Try each one and do a sizeof(struct xxx) and print the size.  If it is packed it should be the sum of the data types in the struct.  If not, there will be extra bytes in the size.

The compiler shouldn't complain if you pick the right one.

---

### Post by johnl on 2009-08-06
Hi,

#pragma directives are compiler dependant.  MSVC uses #pragma pack to set structure alignment.

the __attribute__ syntax is a GCC extension.  So to set structure alignment is somewhat compiler dependant:

Here's a pair of examples:

GCC:
```

typedef struct foobar_s {
    char   a;
    int    b;
    double c;
} __attribute__((packed)) foobar_t;

// or alternately
struct __attribute__((packed)) foobar_s {
    char   a;
    int    b;
    double c;
} ;

```

MSVC:

```

#pragma pack(push, 1) // store previous pack value
                      // and set new value to 1 (no alignment)
struct foobar_s {
    char   a;
    int    b;
    double c;
} ;
#pragma pack(pop)     // restore previous pack value

```


With that said, newer GCC versions might support the MSVC syntax.

Hope this helps.

---

### Post by dwhitney67 on 2009-08-06
I've used #pragma pack(1), and its complement #pragma pack(0), successfully with GCC.

Example:
```

#include <cassert>

#pragma pack(1)

struct Foo
{
   int  value1;
   char value2;
   int  value3;
};

#pragma pack(0)

int main()
{
   assert(sizeof(Foo) == 9);
}

```

---

### Post by Volt9000 on 2009-08-06
Thanks for the responses.

So if pack(1) specifies a 1-byte alignment boundary, what does pack(0) do? Turn off packing completely, and let the compiler determine how to align the struct?

---

### Post by dwhitney67 on 2009-08-06
pack(1) enables the packing feature, pack(0) disables it.  At least that's how I interpret it.

---

### Post by johnl on 2009-08-06
Hi,

Check out [this page](http://msdn.microsoft.com/en-us/library/2e70t5y1%28VS.80%29.aspx) for the MSVC #pragma pack.

basically the value you give to pack() is the byte alignment.  When you specify pack(1) that means align on 1-byte boundaries, effectively disabling alignment.

> 
Specifies the value, in bytes, to be used for packing. The default value for n is 8. Valid values are 1, 2, 4, 8, and 16. The alignment of a member will be on a boundary that is either a multiple of n or a multiple of the size of the member, whichever is smaller.



GCC's behavior may be different.

---

### Post by Volt9000 on 2009-08-06
Thanks for the feedback everyone.

Now, regardless of which I use, I only need to apply the packing to the entire structure, and not to each individual element, right?

I only ask because I have someone else's code here that has something like this:

```

typedef struct
{
  int foo1 __attribute__ ((packed));
  int foo2 __attribute__ ((packed));
  char foo3 __attribute__ ((packed));
} __attribute__ ((packed)) bar;

```

But this isn't necessary, to specify packed for every element, is it?

[edit]
Ok I just tried it out, it seems that it isn't necessary for each individual element. Applying the attribute to the entire struct seems sufficient.

---

