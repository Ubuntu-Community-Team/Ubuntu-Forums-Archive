---
title: "[C/C++] Endian conversion of 64-bit value"
date: 2009-06-18
forum: Programming Talk
---

### Post by dwhitney67 on 2009-06-18
Is there a short-hand way to convert a 64-bit value to the "network ordering" of bytes, which is Big Endian, and then back again to "host ordering", which could either be Big or Little Endian?

I referenced this [web-page]("http://www.ibm.com/developerworks/library/l-port64.html"), and it mentions bswap_64() as available under Linux, but I cannot find a man-page for it.

I suppose I could attempt to write my own htonll() and ntohll() functions, but I hate to reinvent the wheel if this has already been done.

---

### Post by scourge on 2009-06-18
I afraid you'll either have to write it yourself or use a library like Qt or Boost.

In my chess engine Sloppy I have this macro:

```

#define ENDIAN_SWAP_U64(val) ((U64) ( \
    (((U64) (val) & (U64) 0x00000000000000ff) << 56) | \
    (((U64) (val) & (U64) 0x000000000000ff00) << 40) | \
    (((U64) (val) & (U64) 0x0000000000ff0000) << 24) | \
    (((U64) (val) & (U64) 0x00000000ff000000) <<  8) | \
    (((U64) (val) & (U64) 0x000000ff00000000) >>  8) | \
    (((U64) (val) & (U64) 0x0000ff0000000000) >> 24) | \
    (((U64) (val) & (U64) 0x00ff000000000000) >> 40) | \
    (((U64) (val) & (U64) 0xff00000000000000) >> 56)))

```

U64 is just a typedef to 64-bit integer.


EDIT: Or if you don't care about cross-platform compatibility you can check out /usr/include/endian.h

---

### Post by dwhitney67 on 2009-06-18
scourge

Thanx for the reply.  I found another solution, which I have incorporated into my code (and tested).

Basically it takes a 64-bit number with the following layout:

AB CD EF GH IJ KL MN OP

and converts it to:

OP MN KL IJ GH EF CD AB


```

   uint64_t ntohll(const uint64_t value) const
   {
      enum { TYP_INIT, TYP_SMLE, TYP_BIGE };

      union
      {
         uint64_t ull;
         uint8_t  c[8];
      } x;

      // Test if on Big Endian system.
      static int typ = TYP_INIT;

      if (typ == TYP_INIT)
      {
         x.ull = 0x01;
         typ = (x.c[7] == 0x01) ? TYP_BIGE : TYP_SMLE;
      }

      // System is Big Endian; return value as is.
      if (typ == TYP_BIGE)
      {
         return value;
      }

      // else convert value to Big Endian
      x.ull = value;

      int8_t c = 0;
      c = x.c[0]; x.c[0] = x.c[7]; x.c[7] = c;
      c = x.c[1]; x.c[1] = x.c[6]; x.c[6] = c;
      c = x.c[2]; x.c[2] = x.c[5]; x.c[5] = c;
      c = x.c[3]; x.c[3] = x.c[4]; x.c[4] = c;

      return x.ull;
   }

   uint64_t htonll(const uint64_t value) const
   {
      return ntohll(value);
   }

```

---

