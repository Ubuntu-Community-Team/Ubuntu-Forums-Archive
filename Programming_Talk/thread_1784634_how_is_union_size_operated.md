---
title: "how is union size operated"
date: 2011-06-17
forum: Programming Talk
---

### Post by jamesbon on 2011-06-17
When we declare union in C, how is the size of union allocated in the
memory?

---

### Post by dwhitney67 on 2011-06-17
Declaring a union and instantiating it are two different things.

If you declare a union, and want to determine its size, then use the sizeof() operator.

Whether you instantiate an object of the union type on the stack or on the heap is up to you.  As for the how it is laid out in memory, it is no different than any other block of byte(s).

The purpose of a union is to allow the programmer to interpret the same data space using two or more types.  The largest declared type will dictate the size of the union.

With a mixed bag of types such as in the following, the union will have a size of 128 bytes, because the last type is by far the largest type, and this is the necessary space required to hold that type.
```

typedef union
{
   int8_t     sbyte;
   uint8_t    ubyte;
   int16_t    sshort;
   uint16_t   ushort;
   int32_t    slong;
   uint32_t   ulong;
   uint64_t   ulonglong;
   char       cstr[128];
} Data;


Data data;   // here, with the instantiation of the object, 128 bytes are laid out on the stack

```

---

### Post by jamesbon on 2011-06-17
Ohh thanks I was confused with some heap kind of memory structure and had thought it in that direction.

---

