---
title: "Approach to simulate floating point numbers"
date: 2012-05-02
forum: Programming Talk
---

### Post by DaviesX on 2012-05-02
This problem confuses me for a long time, so I decided to spend a whole night to simulate this process. And with an effort, I did it, not perfect, though.

It can't process 0.0f correctly(0.0f = 1.0f :mad:), and it is slow either.

```

#include <stdio.h>

float GenerateFloat ( int integer, float fraction )
{
// 1    8        23
// sign exponent fraction
// 0	10101010 110001000100010001000001
// single float

    unsigned long decimal = 0;
    unsigned long exactNumber = 0;
    long numBits = 0, firstValid = 0;

    // Covert the fraction part to binary form
    while ( fraction != 0.0f && numBits < 23 )
    {
        fraction *= 2.0f;
        numBits ++;

        // 0 or 1
        if ( fraction >= 1.0f )
        {
            decimal |= 1 << (23 - numBits);
            fraction -= 1.0f;

            // The position of the first non-zero number
            if ( firstValid == 0 )
                firstValid = numBits;

        }// End If

    }// End While

    // Determine the sign
    if ( integer < 0 )
    {
        exactNumber |= 0X80000000;
        integer = -integer;

    }// End If

    unsigned long exponent = 127;

    // Scale the decimal to 1.xxxx * 2^M form, and 1 is ignored in actually formating
    if ( integer > 0 )
    {
        // IntegerBits - 1
        int nInteger = 0;
        for ( int temp = integer; temp > 1; temp >>= 1, nInteger ++ );

        // Float part 0.1101001
        // Integer part 10010
        // Merge 10010.1101001 = 1.00101101001 * 2^4
        if ( nInteger <= 23 )
        {
            exactNumber |= (integer << (23 - nInteger) |
                            (decimal >> nInteger)) & (0X7FFFFF);
        }
        else
        {
            exactNumber |= (integer >> (nInteger - 23)) & (0X7FFFFF);

        }// End If

        exponent += nInteger;
    }
    else
    {
        // Float part 0.00001101001
        // Change of the expression 0.00001101001 = 1.101001 * 2^(-5)
        exactNumber |= (decimal << firstValid)  & (0X7FFFFF);
        exponent -= firstValid;

    }// End If

    // Merge the exponent
    exactNumber |= exponent << (32 - 8 - 1);

    return (float &)exactNumber;
}

int main ( void )
{
    float fNumber = GenerateFloat ( 12, 0.04f );
    printf ( "%f\n", fNumber );

    return 0;
}

```

---

### Post by DaviesX on 2012-05-02
Have no idea how to do with 0 :mad: just make a hard code for it ...
```

#include <stdio.h>

float GenerateFloat ( int integer, float fraction )
{
// 1    8        23
// sign exponent fraction
// 0	10101010 11000100010001000100010
// single float

    // 0 00000000 00000000000000000000000
    if ( integer == 0 && fraction == 0 )
        return 0.0f;

    unsigned long decimal = 0;
    unsigned long exactNumber = 0;
    long numBits = 0, firstValid = 0;

    // Covert the fraction part to binary form
    while ( fraction != 0.0f && numBits < 23 )
    {
        fraction *= 2.0f;
        numBits ++;

        // 0 or 1
        if ( fraction >= 1.0f )
        {
            decimal |= 1 << (23 - numBits);
            fraction -= 1.0f;

            // The position of the first non-zero number
            if ( firstValid == 0 )
                firstValid = numBits;

        }// End If

    }// End While

    // Determine the sign
    if ( integer < 0 )
    {
        exactNumber |= 0X80000000;
        integer = -integer;

    }// End If

    unsigned long exponent = 127;

    // Scale the decimal to 1.xxxx * 2^M form, and 1 is ignored in actually formating
    if ( integer > 0 )
    {
        // IntegerBits - 1
        int nInteger = 0;
        for ( int temp = integer; temp > 1; temp >>= 1, nInteger ++ );

        // Float part 0.1101001
        // Integer part 10010
        // Merge 10010.1101001 = 1.00101101001 * 2^4
        if ( nInteger <= 23 )
        {
            exactNumber |= (integer << (23 - nInteger) |
                            (decimal >> nInteger)) & (0X7FFFFF);
        }
        else
        {
            exactNumber |= (integer >> (nInteger - 23)) & (0X7FFFFF);

        }// End If

        exponent += nInteger;
    }
    else
    {
        // Float part 0.00001101001
        // Change of the expression 0.00001101001 = 1.101001 * 2^(-5)
        exactNumber |= (decimal << firstValid)  & (0X7FFFFF);
        exponent -= firstValid;

    }// End If

    // Merge the exponent
    exactNumber |= exponent << (32 - 8 - 1);

    return (float &)exactNumber;
}

int main ( void )
{
    float fNumber = GenerateFloat ( 0, 0.123456f );
    printf ( "%f\n", fNumber );

    return 0;
}


```

---

### Post by Bachstelze on 2012-05-02
What is it even supposed to do?

---

### Post by DaviesX on 2012-05-03
Oh, just stimulate how to encode a IEEE floating point, but I suppose to mess up something, cause 0.0f doesn't work

---

### Post by Bachstelze on 2012-05-03
That's not your only problem. :p For starters, it does not even compile...

---

### Post by jim_24601 on 2012-05-03
> **DaviesX said:**
> Have no idea how to do with 0 :mad: just make a hard code for it ...

You have in fact hit upon the correct answer. Zero is a special case in IEEE floating point format (though you can treat it as a special case of denormalised numbers, when you support those).

I think you've got a problem with your initial normalising loop though. If your fractional part is less than 0.5, you'll lose precision because the loop cuts out after 23 shifts no matter how small the number.

I wouldn't use a float for the fractional part at all, though I know why you're doing so. If I were making a project to generate IEEE floating-point numbers, I'd use fixed point. You'd need a fairly wide data type to represent the full range even of a single-precision float, though :)

Also, what is this?
```

    return (float &)exactNumber;

```

It doesn't look like legal C to me, is your compiler allowing it as an extension? In C it would be
```

    return *(float*)(&exactNumber);

```

---

### Post by DaviesX on 2012-05-03
Oh, that is gcc but compiled as c++ code, 
And I use C flag just now, and it still passed. It means regarding that 4-byte data as a float. I saw this sort of expression while I was reading the others code. I don't know if it is standardized...

---

### Post by Bachstelze on 2012-05-03
It compiles with g++, not with gcc. That means it's C++, not C, so I can't comment on it since I don't know C++. :p

---

### Post by PeterP24 on 2012-05-03
> **Bachstelze said:**
> It compiles with g++, not with gcc. That means it's C++, not C, so I can't comment on it since I don't know C++. :p

It looks like C to me. I know that a C++ compiler would compile only very strict abiding to standard C programs. Well - don't take me too seriously - I only find that out by using an Android app which promises me how to consider an "C++ code mixed with C code program". Never applied this advice in combat since I consider C++ code to differ in a very substantial way from C - I never plan to write C code mixed with C++ code.

---

### Post by DaviesX on 2012-05-03
haha, that is because I learnt C++ half way before, so I often mix C with C++ grammar...

---

### Post by Bachstelze on 2012-05-03
> **PeterP24 said:**
> It looks like C to me.

Yes, but it's not, because of this line:

```
    return (float &)exactNumber;
```

which is definitely not legal C, but seems to be legal C++ since g++ compiles it without any complaint.

---

### Post by DaviesX on 2012-05-03
I have thought about it for a whole day, but I can't come up with a good solution :mad: can you help me with it ?
How can I deal with a huge number or a extremely small number like 1e-20

---

### Post by DaviesX on 2012-05-03
I change to code like this, 
```

#include <stdio.h>

inline int IntPowerFunction ( int base, int exponent )
{
    int result = base;
    for ( int i = 1; i < exponent; i++ )
        result *= base;

    return result;
}

float GenerateFloat ( int base, int dExponent )
{
// 1    8        23
// sign exponent fraction
// 0	10101010 11000100010001000100010
// single float

    // 0 00000000 00000000000000000000000
    if ( base == 0 )
        return 0.0f;

    if ( dExponent == 0 )
        return 1.0f;

    unsigned long exactNumber = 0;
    unsigned long decimal = 0;

    // Determine the sign
    if ( base < 0 )
    {
        exactNumber |= 0X80000000;
        base = -base;

    }// End If

    unsigned long evaluate;
    unsigned long fraction, integer;
    long numBits, firstValid, remains;

    // Separate the integer
    if ( dExponent > 0 )
    {
        evaluate = IntPowerFunction ( 10, dExponent );
        integer = base*evaluate;
        fraction = 0;
    }
    else
    {
        evaluate = IntPowerFunction ( 10, -dExponent );
        fraction = base % evaluate;
        integer = (base - fraction)/evaluate;

        firstValid = 0;
        remains= 23;

        // Covert the fraction part to binary form
        while ( fraction != 0 && remains > 0 )
        {
            fraction <<= 1;
            remains --;

            // 0 or 1
            if ( fraction >= evaluate )
            {
                // The position of the first non-zero number
                if ( firstValid == 0 )
                {
                    firstValid = 23 - remains;
                    remains = 23 - 1;

                }// End If

                decimal |= 1 << remains;
                fraction -= evaluate;

            }// End If

        }// End While

        numBits = 23 - remains;

    }// End If

    unsigned long exponent = 127;

    // Scale the decimal to 1.xxxx * 2^M form, and 1 is ignored in actually formating
    if ( integer > 0 )
    {
        // IntegerBits - 1
        int nInteger = 0;
        for ( int temp = integer; temp > 1; temp >>= 1, nInteger ++ );
        exponent += nInteger;

        // 0.1101001 * 2^2 = 0.0011010 * 2^0
        decimal >>= firstValid - 1;

        // Float part 0.1101001
        // Integer part 10010
        // Merge 10010.1101001 = 1.00101101001 * 2^4
        if ( nInteger <= 23 )
        {
            exactNumber |= (integer << (23 - nInteger) |
                            (decimal >> nInteger)) & (0X7FFFFF);
        }
        else
        {
            exactNumber |= (integer >> (nInteger - 23)) & (0X7FFFFF);

        }// End If
    }
    else
    {
        // Float part 0.00001101001
        // Change of the expression 0.00001101001 -> 0.1101001 * 2^(-6) = 1.101001 * 2^(-5)
        exactNumber |= (decimal << 1)  & (0X7FFFFF);
        exponent -= firstValid;

    }// End If

    // Merge the exponent
    exactNumber |= exponent << (32 - 8 - 1);
    return *(float *)&exactNumber;
}

int main ( void )
{
    // 1204 * 10^(-2)
    printf ( "%f\n", GenerateFloat ( 1204, -2 ) );
    return 0;
}

```

---

