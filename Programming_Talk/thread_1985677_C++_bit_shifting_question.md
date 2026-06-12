---
title: "C++ bit shifting question"
date: 2012-05-23
forum: Programming Talk
---

### Post by Kentucky88 on 2012-05-23
[PHP]
unsigned int convert_bin2dec(bool[] &bitarray, unsigned int lengthofbitarray)
{
	unsigned int result = 0;
	
	for(unsigned int n=0; n < lengthofbitarray; n++)
	{
		result <<= 1; //shift result to the left by 1
		if(bitarray[n]) result = (result | 1);
		else result = (result | 0);
	}
	return result;
}[/PHP]

The function above is supposed to take an array of bool which represents an unsigned integer encoded in binary.  Assume that the length of the bool array is less than sizeof(unsigned int).  Also assume that the least significant bit is at position 0 in the boolean array.  The function above is used heavily so I want to make it as efficient as possible.  Does anyone see a way to make it more efficient (assume modern X86 processor).  Should I just use bitset?

[http://www.cplusplus.com/reference/stl/bitset/](http://www.cplusplus.com/reference/stl/bitset/)

---

### Post by dwhitney67 on 2012-05-23
Take this statement out:
```

else result = (result | 0);

```
It accomplishes nothing.

You could also compare your function to this one, although it is probably as inefficient because it performs shifts on zero and the ORing (which I indicated above is not necessary):
```

unsigned int convert_bin2dec(bool bitarray[], const int lengthOfArray)
{
    unsigned int result = 0;

    for (int i = 0; i < lengthOfArray; ++i)
    {
        result |= (bitarray[i] << i);
    }

    return result;
}

```

---

### Post by kingtaurus on 2012-05-24
> **dwhitney67 said:**
> Take this statement out:
```

else result = (result | 0);

```
It accomplishes nothing.

You could also compare your function to this one, although it is probably as inefficient because it performs shifts on zero and the ORing (which I indicated above is not necessary):
```

unsigned int convert_bin2dec(bool bitarray[], const int lengthOfArray)
{
    unsigned int result = 0;

    for (int i = 0; i < lengthOfArray; ++i)
    {
        result |= (bitarray[i] << i);
    }

    return result;
}

```

(1) I'm confused. Based upon the method name, it looks like you are trying to convert a binary representation of a number to an unsigned int. If you want to do this, you have to guarantee that the sizeof(unsigned int)*(#bits in a byte on this platform) > lengthOfArray . 

 "addressable unit of data storage large enough to hold any member of the basic character set of the execution environment" == 1 byte (there are platforms with bytes being, 8,16, ...)

(2) Why do you have a bitarray to begin with? You can just use an unsigned int as that bit array. If you need to check if a bit is set (say the n-th bit):
```

//
unsigned int a;
//
//.. fill a (using:
// a |= 1 << __bit_to_set__;
//

//
if ( a & (1 << n) )
{
//bit is SET
}
else
{
//bit is NOT set
}

```

---

### Post by MadCow108 on 2012-05-24
as you mentioned modern x86, you can do it in two pmovmskb (sse2) instructions (+ 2 loads)
```

#include <emmintrin.h>
(_mm_movemask_epi8((__m128i)*(__m128i*)a)) | 
    (_mm_movemask_epi8((__m128i)*(__m128i*)(a+16) << 16))

```

though the most significant bit must be set
with aligned memory its ~20 times faster.

use _mm_loadu_si128 if a is not aligned to 16 byte.

avx2 will have _mm256_movemask_epi8 for 32 byte at once and good unaligned memory access performance. Though I don't think cpus with that are wide spread yet (if their even on the market already)

---

