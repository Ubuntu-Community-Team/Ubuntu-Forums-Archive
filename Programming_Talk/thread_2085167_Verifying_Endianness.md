---
title: "Verifying Endianness"
date: 2012-11-17
forum: Programming Talk
---

### Post by 3246251196 on 2012-11-17
I believe are linux commands that can output the value of endianness.

Would it also be true to assume that a bitwise shift left will indicate the value of endianness? Where given a integral value value, v, and a number of left shifts, n, if (v * n^2) > v this implies Big Endian and vice versa?

---

### Post by zobayer1 on 2012-11-17
I don't know about commands, but this code should determine the endianness
```

#define BIG_ENDIAN 0
#define LITTLE_ENDIAN 1

int TestByteOrder() {
    short int word = 0x0001;
    char *byte = (char *) &word;
    return (byte[0] ? LITTLE_ENDIAN : BIG_ENDIAN);
}

```

---

### Post by Bachstelze on 2012-11-17
> **3246251196 said:**
> 
Would it also be true to assume that a bitwise shift left will indicate the value of endianness? Where given a integral value value, v, and a number of left shifts, n, if (v * n^2) > v this implies Big Endian and vice versa?

If you mean in C, it's a big no! All operators in C work on values, not bits. (1 << 5) will always be 32, regardless of endianness. One way to test for it is:

```

unsigned int n = 1;
bool islittle = *((unsigned char*)(&n)) == 1;
```

---

### Post by 3246251196 on 2012-11-17
Thank you for your two replies. Identical.

We are saying:
1- Here is a 4 byte integer
2- Let the first byte (lowest address) of the memory that stores integer be converted to a character (so as to represent 1 byte)
3- If this byte, when de-referenced, contains the value  1, then we are working with little, else big.

---

### Post by zobayer1 on 2012-11-17
> **3246251196 said:**
> Thank you for your two replies. Identical.

We are saying:
1- Here is a 4 byte integer
2- Let the first byte (lowest address) of the memory that stores integer be converted to a character (so as to represent 1 byte)
3- If this byte, when de-referenced, contains the value  1, then we are working with little, else big.

Yes, and [Bachstelze]("http://ubuntuforums.org/member.php?u=51114") explained why bit shifting won't work, even if they seem correct theoretically.

---

