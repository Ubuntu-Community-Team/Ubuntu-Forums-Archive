---
title: "[C++] Encoding Values in Big Endian Format"
date: 2009-06-26
forum: Programming Talk
---

### Post by dwhitney67 on 2009-06-26
I wrote a small program to test whether I understood Big Endian formatting vs. Little Endian.

I know that when sending raw data across a socket, that it is best to convert that data to network-byte-order, or Big Endian.

Well, with the results of the program below, I have managed to confuse myself.  Can someone tell me which of the last two values of the output is correct?

BigEndianTest.cpp
```

#include <string>
#include <iostream>
#include <cstring>
#include <stdint.h>
#include <arpa/inet.h>

typedef union
{
   int8_t     sbyte;
   uint8_t    ubyte;
   int16_t    sshort;
   uint16_t   ushort;
   int32_t    slong;
   uint32_t   ulong;
   uint64_t   ulonglong;
   char       str[127];
} ValueTypes;

struct Value
{
   Value() { clear(); }
   void clear() { memset(&vt, 0, sizeof(ValueTypes)); }

   ValueTypes vt;
};

typedef std::basic_string<uint8_t> RawData;

int main()
{
   Value value;
   value.vt.ushort = 0xCAFE;

   uint16_t bigEnd = htons(value.vt.ushort);

   std::cout << std::hex << value.vt.ushort << ", " << bigEnd << std::dec << std::endl;

   uint8_t* ptr1 = reinterpret_cast<uint8_t*>(&bigEnd);
   uint8_t* ptr2 = reinterpret_cast<uint8_t*>(&value.vt.ushort);

   RawData  rd1(ptr1, ptr1 + sizeof(bigEnd));
   RawData  rd2(ptr2, ptr2 + sizeof(value.vt.ushort));

   std::cout << std::hex << (uint32_t) rd1[0] << " " << (uint32_t) rd1[1] << std::dec << std::endl;
   std::cout << std::hex << (uint32_t) rd2[0] << " " << (uint32_t) rd2[1] << std::dec << std::endl;
}

```

Output:
```

cafe, feca
ca fe
fe ca

```
My gut instinct is that the correct answer is "ca fe", but the value for bigEnd appears different, thus the cause of the confusion.

---

### Post by movieman on 2009-06-27
> **dwhitney67 said:**
> My gut instinct is that the correct answer is "ca fe", but the value for bigEnd appears different, thus the cause of the confusion.

By definition, a short is always in the correct format: it's only when you write that short to memory that big/little endian matters.

When you call htons() on a little-endian machine, it will do a byte swap so that when you write that value to memory you end up with big-endian values _in memory_. If you then read those values out as a little-endian short, they will be byte-swapped.

The idea is that if you have a structure which contains shorts, and that must be passed over the network in big-endian byte order, you write your shorts to that structure using htons to byte-swap them. The structure will then look like garbage to the host CPU, but will be interpreted correctly by the other end.

---

