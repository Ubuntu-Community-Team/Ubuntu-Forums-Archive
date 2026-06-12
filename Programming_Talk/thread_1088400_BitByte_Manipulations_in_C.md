---
title: "Bit/Byte Manipulations in C"
date: 2009-03-06
forum: Programming Talk
---

### Post by era86 on 2009-03-06
Greetings!

I have a quick question that seems a bit difficult to google, or maybe I didn't try hard enough.  Anyway, I want to know what happens if I have an unsigned short pointer (u16) and increment it on a unsigned char (u8) buffer.

For example:
[PHP]
unsigned short * num;
unsigned char buf[1024];
num = buf;
num++;

[/PHP]

Does this increment a whole 2 bytes?  Would I go from byte 0 to byte 2?

Thanks in advance!

---

### Post by movieman on 2009-03-06
> **era86 said:**
> Does this increment a whole 2 bytes?  Would I go from byte 0 to byte 2?

Yes.

---

### Post by era86 on 2009-03-06
Sweet.  And...

When I cast a u16 to a u8, which bits are cut out of it?  For example:

[PHP]
u16 var16 = 0x00FF;
u8 var8 = (u8)var16;
[/PHP]

Do I get the 0x00 or the 0xFF?

---

### Post by dwhitney67 on 2009-03-06
era86

Would it kill you to write a 10 line program to figure this out on your own?

If you have a 16-bit value, why don't you tell me which portion of it you want to assign to your 8-bit value... do you want to MSB or the LSB?  Depending on what you want, then assign your 8-bit value appropriately, without performing a "lame" cast.  For example:
```

#include <stdint.h>
...
uint16_t two_bytes     = 0xDEAD;
uint8_t  one_byte_LSB  = two_bytes & 0xFF;             // obtains the LSB
uint8_t  one_byte_MSB  = (two_bytes & 0xFF00) >> 8;    // obtains the MSB

```

P.S.
MSB = Most Significant Byte
LSB = Least Significant Byte

P.S.S.
```

#include <stdint.h>
#include <assert.h>

int main()
{
  uint16_t value = 0xDEAD;
  assert((uint8_t)value == 0xAD);
}

```

---

### Post by uljanow on 2009-03-06
> **era86 said:**
> Sweet.  And...

When I cast a u16 to a u8, which bits are cut out of it?  For example:

[PHP]
u16 var16 = 0x00FF;
u8 var8 = (u8)var16;
[/PHP]

Do I get the 0x00 or the 0xFF?

That depends on the endianness of the machine.

---

### Post by movieman on 2009-03-06
> **uljanow said:**
> That depends on the endianness of the machine.

No, you'll always get the low byte if you cast a u16 value to u8.

I think you're confusing it with casting pointers, where the value of the byte at the address the u16 pointer pointed to would depend on the endianness.

i.e.

u16 foo
u8* bar = (u8 *) &foo;

*bar could be either high or low byte depending on the machine.

---

### Post by era86 on 2009-03-06
> **dwhitney67 said:**
> era86

Would it kill you to write a 10 line program to figure this out on your own?

If you have a 16-bit value, why don't you tell me which portion of it you want to assign to your 8-bit value... do you want to MSB or the LSB?  Depending on what you want, then assign your 8-bit value appropriately, without performing a "lame" cast.  For example:
```

#include <stdint.h>
...
uint16_t two_bytes     = 0xDEAD;
uint8_t  one_byte_LSB  = two_bytes & 0xFF;             // obtains the LSB
uint8_t  one_byte_MSB  = (two_bytes & 0xFF00) >> 8;    // obtains the MSB

```

P.S.
MSB = Most Significant Byte
LSB = Least Significant Byte

P.S.S.
```

#include <stdint.h>
#include <assert.h>

int main()
{
  uint16_t value = 0xDEAD;
  assert((uint8_t)value == 0xAD);
}

```

Thank you for your help.  I thought someone might know on the top of their head, so I didn't bother to think if it would kill me to write a quick program.  If it makes you feel better, I had figured this out on my own either way doing some very similar bit operations myself.

> **movieman said:**
> No, you'll always get the low byte if you cast a u16 value to u8.

I think you're confusing it with casting pointers, where the value of the byte at the address the u16 pointer pointed to would depend on the endianness.

i.e.

u16 foo
u8* bar = (u8 *) &foo;

*bar could be either high or low byte depending on the machine.

Hmmm.  I might look into this.  I'm getting errors in my code and I do this alot.  I'm guessing this is not good practice?

---

