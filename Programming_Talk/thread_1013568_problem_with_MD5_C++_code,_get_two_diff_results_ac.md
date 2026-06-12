---
title: "problem with MD5 C++ code, get two diff results across Ubuntu OS's"
date: 2008-12-17
forum: Programming Talk
---

### Post by jmartrican on 2008-12-17
Hello,

I am using the follow MD5 code for C++.  [http://www.md5hashing.com/c++/](http://www.md5hashing.com/c++/)  Specifically the md5 and m5wrapper code.

I developed software in Ubuntu 7.10 (gcc 4.2.1) that uses the mentioned MD5 source code.  It works well.  I use it for SIP authentication against a SIP voip service-provider's proxy servers and I am able to authenticate (meaning I digest the given challenge data in the SIP 401 response with my password and I resend my REGISTER request and get back a 200 OK... for the SIP folks out there).

When I run the same code in Ubuntu 8.04.1 (gcc 4.2.3) I get different md5 digest results that are wrong, since my code fails to authenticate against the SIP proxy server I am pointing it to.  I took the same credentials from the failed tests on Ubuntu 8 and re-hashed them on my Ubuntu 7 box and the results were diff.  Since I never had a problem with authenticating with Ubuntu 7 using said code, I presume the Ubuntu 8 results are wrong.

Can anyone imagine what could be causing this discrepancy?  What could be causing the MD5 code (its in the link posted above) to give different results under the two different Ubuntu/gcc versions?  Could it be some low level math operations used in the md5.cpp code?

Thanks a lot!!!!

---

### Post by jmartrican on 2008-12-17
After doing some research it looks like the problem is in these macros.

in md5.cpp... macros defined
```

// Constants for MD5Transform routine.
#define S11 7
#define S12 12
#define S13 17
#define S14 22
#define S21 5
#define S22 9
#define S23 14
#define S24 20
#define S31 4
#define S32 11
#define S33 16
#define S34 23
#define S41 6
#define S42 10
#define S43 15
#define S44 21

/* F, G, H and I are basic MD5 functions. */
#define F(x, y, z) (((x) & (y)) | ((~x) & (z)))
#define G(x, y, z) (((x) & (z)) | ((y) & (~z)))
#define H(x, y, z) ((x) ^ (y) ^ (z))
#define I(x, y, z) ((y) ^ ((x) | (~z)))

/* ROTATE_LEFT rotates x left n bits. */
#define ROTATE_LEFT(x, n) (((x) << (n)) | ((x) >> (32-(n))))

/*
FF, GG, HH, and II transformations for rounds 1, 2, 3, and 4.
Rotation is separate from addition to prevent recomputation.
*/
#define FF(a, b, c, d, x, s, ac) { \
 (a) += F ((b), (c), (d)) + (x) + (unsigned long int)(ac); \
 (a) = ROTATE_LEFT ((a), (s)); \
 (a) += (b); \
  }

#define GG(a, b, c, d, x, s, ac) { \
 (a) += G ((b), (c), (d)) + (x) + (unsigned long int)(ac); \
 (a) = ROTATE_LEFT ((a), (s)); \
 (a) += (b); \
  }
#define HH(a, b, c, d, x, s, ac) { \
 (a) += H ((b), (c), (d)) + (x) + (unsigned long int)(ac); \
 (a) = ROTATE_LEFT ((a), (s)); \
 (a) += (b); \
  }
#define II(a, b, c, d, x, s, ac) { \
 (a) += I ((b), (c), (d)) + (x) + (unsigned long int)(ac); \
 (a) = ROTATE_LEFT ((a), (s)); \
 (a) += (b); \
  }

```

here is where the macros are used in the MD5Transform function.
```

/*
 * MD5 basic transformation. Transforms state based on block.
 */
void MD5::MD5Transform (unsigned long int state[4], unsigned char block[64])
{
    std::cout<<"\n--IN MD5Transform--\n";

        unsigned long int a = state[0], b = state[1], c = state[2], d = state[3], x[16];

        Decode (x, block, 64);

        /* Round 1 */
        FF (a, b, c, d, x[ 0], S11, 0xd76aa478); /* 1 */
        FF (d, a, b, c, x[ 1], S12, 0xe8c7b756); /* 2 */
        FF (c, d, a, b, x[ 2], S13, 0x242070db); /* 3 */
        FF (b, c, d, a, x[ 3], S14, 0xc1bdceee); /* 4 */
        FF (a, b, c, d, x[ 4], S11, 0xf57c0faf); /* 5 */
        FF (d, a, b, c, x[ 5], S12, 0x4787c62a); /* 6 */
        FF (c, d, a, b, x[ 6], S13, 0xa8304613); /* 7 */
        FF (b, c, d, a, x[ 7], S14, 0xfd469501); /* 8 */
        FF (a, b, c, d, x[ 8], S11, 0x698098d8); /* 9 */
        FF (d, a, b, c, x[ 9], S12, 0x8b44f7af); /* 10 */
        FF (c, d, a, b, x[10], S13, 0xffff5bb1); /* 11 */
        FF (b, c, d, a, x[11], S14, 0x895cd7be); /* 12 */
        FF (a, b, c, d, x[12], S11, 0x6b901122); /* 13 */
        FF (d, a, b, c, x[13], S12, 0xfd987193); /* 14 */
        FF (c, d, a, b, x[14], S13, 0xa679438e); /* 15 */
        FF (b, c, d, a, x[15], S14, 0x49b40821); /* 16 */

        /* Round 2 */
        GG (a, b, c, d, x[ 1], S21, 0xf61e2562); /* 17 */
        GG (d, a, b, c, x[ 6], S22, 0xc040b340); /* 18 */
        GG (c, d, a, b, x[11], S23, 0x265e5a51); /* 19 */
        GG (b, c, d, a, x[ 0], S24, 0xe9b6c7aa); /* 20 */
        GG (a, b, c, d, x[ 5], S21, 0xd62f105d); /* 21 */
        GG (d, a, b, c, x[10], S22,  0x2441453); /* 22 */
        GG (c, d, a, b, x[15], S23, 0xd8a1e681); /* 23 */
        GG (b, c, d, a, x[ 4], S24, 0xe7d3fbc8); /* 24 */
        GG (a, b, c, d, x[ 9], S21, 0x21e1cde6); /* 25 */
        GG (d, a, b, c, x[14], S22, 0xc33707d6); /* 26 */
        GG (c, d, a, b, x[ 3], S23, 0xf4d50d87); /* 27 */

        GG (b, c, d, a, x[ 8], S24, 0x455a14ed); /* 28 */
        GG (a, b, c, d, x[13], S21, 0xa9e3e905); /* 29 */
        GG (d, a, b, c, x[ 2], S22, 0xfcefa3f8); /* 30 */
        GG (c, d, a, b, x[ 7], S23, 0x676f02d9); /* 31 */
        GG (b, c, d, a, x[12], S24, 0x8d2a4c8a); /* 32 */

        /* Round 3 */
        HH (a, b, c, d, x[ 5], S31, 0xfffa3942); /* 33 */
        HH (d, a, b, c, x[ 8], S32, 0x8771f681); /* 34 */
        HH (c, d, a, b, x[11], S33, 0x6d9d6122); /* 35 */
        HH (b, c, d, a, x[14], S34, 0xfde5380c); /* 36 */
        HH (a, b, c, d, x[ 1], S31, 0xa4beea44); /* 37 */
        HH (d, a, b, c, x[ 4], S32, 0x4bdecfa9); /* 38 */
        HH (c, d, a, b, x[ 7], S33, 0xf6bb4b60); /* 39 */
        HH (b, c, d, a, x[10], S34, 0xbebfbc70); /* 40 */
        HH (a, b, c, d, x[13], S31, 0x289b7ec6); /* 41 */
        HH (d, a, b, c, x[ 0], S32, 0xeaa127fa); /* 42 */
        HH (c, d, a, b, x[ 3], S33, 0xd4ef3085); /* 43 */
        HH (b, c, d, a, x[ 6], S34,  0x4881d05); /* 44 */
        HH (a, b, c, d, x[ 9], S31, 0xd9d4d039); /* 45 */
        HH (d, a, b, c, x[12], S32, 0xe6db99e5); /* 46 */
        HH (c, d, a, b, x[15], S33, 0x1fa27cf8); /* 47 */
        HH (b, c, d, a, x[ 2], S34, 0xc4ac5665); /* 48 */

        /* Round 4 */
        II (a, b, c, d, x[ 0], S41, 0xf4292244); /* 49 */
        II (d, a, b, c, x[ 7], S42, 0x432aff97); /* 50 */
        II (c, d, a, b, x[14], S43, 0xab9423a7); /* 51 */
        II (b, c, d, a, x[ 5], S44, 0xfc93a039); /* 52 */
        II (a, b, c, d, x[12], S41, 0x655b59c3); /* 53 */
        II (d, a, b, c, x[ 3], S42, 0x8f0ccc92); /* 54 */
        II (c, d, a, b, x[10], S43, 0xffeff47d); /* 55 */
        II (b, c, d, a, x[ 1], S44, 0x85845dd1); /* 56 */
        II (a, b, c, d, x[ 8], S41, 0x6fa87e4f); /* 57 */
        II (d, a, b, c, x[15], S42, 0xfe2ce6e0); /* 58 */
        II (c, d, a, b, x[ 6], S43, 0xa3014314); /* 59 */
        II (b, c, d, a, x[13], S44, 0x4e0811a1); /* 60 */
        II (a, b, c, d, x[ 4], S41, 0xf7537e82); /* 61 */
        II (d, a, b, c, x[11], S42, 0xbd3af235); /* 62 */
        II (c, d, a, b, x[ 2], S43, 0x2ad7d2bb); /* 63 */
        II (b, c, d, a, x[ 9], S44, 0xeb86d391); /* 64 */

        std::cout<<"a = "<<a<<",b = "<<b<<",c = "<<c<<",d = "<<d<<"\n";
        state[0] += a;
        state[1] += b;
        state[2] += c;
        state[3] += d;

        /*
         * Zeroize sensitive information.
         */
        MD5_memset ((POINTER)x, 0, sizeof (x));
        std::cout<<"\n--Leaving MD5Transform--\n";

```

I've yet to decipher what all these macros do.  Would someone be able to point out what some of these operations in the macros do and why they would give different results across the Ubuntu 7 and 8 and/or gcc 4.2.1 and 4.2.3 respectively?

Before you ask.  I already verified that the Decode function is not culprit because across both environments it outputs the same numbers.  I used the std::cout statement towards the end of the second code sample to pinpoint that within Transform is where the discrepancies lie.

Thanks a lot!

---

### Post by jmartrican on 2008-12-17
In case anyone cares the problem has been found.  The issue is that the two different environments use different amount of bits for 'long int'.  My Ubuntu 8 box uses 64 bits for 'long int', where as my ubuntu 7 box uses 32 bit ( left out a small detail that my ubuntu 8 box is a 64 bit server).  This md5 code uses 'unsigned long int' a lot.  The code does math operations with big numbers that get truncated when assigned to the 32 bit version of 'long int'.  It seems like the md5 code expects this truncating behavior, which I find strange.  

The issue was fixed by converting all 'long int's to regular int.  I guess for something like this where the number of bits needs to be precise the developer should have used int32_t, which is guaranteed (or so i assume) to be 32 bits.

thanks

---

