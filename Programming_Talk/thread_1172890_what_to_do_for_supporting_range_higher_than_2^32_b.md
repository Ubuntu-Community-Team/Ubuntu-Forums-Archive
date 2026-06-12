---
title: "what to do for supporting range higher than 2^32 bits"
date: 2009-05-29
forum: Programming Talk
---

### Post by nehagupta on 2009-05-29
Hello 
I m using ubuntu 8.04 lts and i m making a program based on public key cryptography my problem is that i want to genrate the random no , keys of size 1024 bit but ubuntu only support 32 bit integer so how can i deal with it?

---

### Post by Habbit on 2009-05-29
Most cryto libraries represent keys as byte arrays (most likely "unsigned char[]" or "uint8_t[]"). If you are using some kind of random function to generate the key - though it is strange that your crypto library lacks such a function - you would have to fill a byte array with the appropiate size, such as this:```
#include <algorithm>

uint8_t my_rand();

void generate_random_key(uint8_t* key, size_t len) {
    std::generate_n(key, len, my_rand);
}
```
Where my_rand is the random function you are using. For example, you could use a Mersenne Twister instead of the system default rand() which is usually unfit for crypto purposes. You need to take into account that most random functions return ints, so you need to either write a "wrapper" that turns that into an uint8_t or. However, if you can ensure that your array is "assimilable" to an int array, that is, has a length that would make it have a whole number of ints *and* it is int-aligned in memory, you could just use generate_n(reinterpret_cast<int*>(key, len/sizeof(int), rand);

The first requirement is usually not a problem since key lengths are usually powers of two or sums thereof, and such they are usually divisible by all common sizes of int (4 is the usual). Guaranteeing alignment, on the other hand, is compiler-dependent for now, but the C++09 standard adds a way to enforce this: ```
// Create a byte array to hold the key so that it is int-aligned
// and has a whole number of ints. Potentially wastes sizeof(int) - 1 bytes
uint8_t [[align(int)]] key[RSA_KEY_LEN + RSA_KEY_LEN % sizeof(int)];

// Then fill it with a random function that produces ints
std::generate_n(reinterpret_cast<int*>(key), sizeof(key)/sizeof(int), rand);

// Enjoy the generated key!
```

---

