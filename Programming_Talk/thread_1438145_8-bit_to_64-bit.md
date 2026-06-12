---
title: "8-bit to 64-bit"
date: 2010-03-24
forum: Programming Talk
---

### Post by Emill on 2010-03-24
Hello. I wonder if there is a fast way to "unpack" a byte into a 64-bit integer.

If the byte looks like this:
01101001
I want the 64-bit integer to look something like this:
00000000 00000001 00000001 00000000 00000001 00000000 00000000 00000001

I am looking for some kind of x86 (or x86_64) assembly instruction. Maybe some mmx or sse-thing. Just something that works...

If I do this code in gcc:
```
(byte&1) | (((byte>>1)&1)<<8) | (((byte>>2)&1)<<16) | (((byte>>3)&1)<<24)
| (((byte>>4)&1)<<32) | (((byte>>5)&1)<<40) | (((byte>>6)&1)<<48) | (((byte>>7)&1)<<56)
```
And compile with -S -O3 -march=native -mmmx -msse -msse2 -msse3, the output of that is 31 rows!! Is there a better way?
And if there is, is there a way to "pack" it again?

---

### Post by MadCow108 on 2010-03-24
First most important aspect:
Have you profiled and found that this code snippet is to slow?
If you can't prove that then don't bother optimizing it.

I'm not aware of an instruction which could do that, but I am also very unexperienced in x86 assembly details.
Is there any reason such an instruction should exist?

you may be able speed this up by using a lookup table and adding values from that table based on the bits of the byte.
This should reduce the number of operations but also may introduce cache misses.
So if this really faster must be benchmarked

---

### Post by johnl on 2010-03-24
Perhaps there's something [here](http://graphics.stanford.edu/~seander/bithacks.html) that you could use.

---

### Post by CptPicard on 2010-03-24
What's wrong with simply always extracting the most significant bit of your 8bit number, ORing that with your 64bit number and then shifting that left by 8 and the 8bit number by one, repeating 8 times? Should fit into a very tiny asm loop.

---

### Post by Lux Perpetua on 2010-03-24
> **MadCow108 said:**
> you may be able speed this up by using a lookup table and adding values from that table based on the bits of the byte.
This should reduce the number of operations but also may introduce cache missesI like this idea. All you need is a 1k lookup table. 

```
uint64_t unpacked_bytes[256] = {
    0x0000000000000000, 0x0000000000000001, 0x0000000000000100, 0x0000000000000101,
    0x0000000000010000, 0x0000000000010001, 0x0000000000010100, 0x0000000000010101,
    0x0000000001000000, 0x0000000001000001, 0x0000000001000100, 0x0000000001000101,
    0x0000000001010000, 0x0000000001010001, 0x0000000001010100, 0x0000000001010101,
    0x0000000100000000, 0x0000000100000001, 0x0000000100000100, 0x0000000100000101,
    0x0000000100010000, 0x0000000100010001, 0x0000000100010100, 0x0000000100010101,
    0x0000000101000000, 0x0000000101000001, 0x0000000101000100, 0x0000000101000101,
    0x0000000101010000, 0x0000000101010001, 0x0000000101010100, 0x0000000101010101,
    0x0000010000000000, 0x0000010000000001, 0x0000010000000100, 0x0000010000000101,
    0x0000010000010000, 0x0000010000010001, 0x0000010000010100, 0x0000010000010101,
    0x0000010001000000, 0x0000010001000001, 0x0000010001000100, 0x0000010001000101,
    0x0000010001010000, 0x0000010001010001, 0x0000010001010100, 0x0000010001010101,
    0x0000010100000000, 0x0000010100000001, 0x0000010100000100, 0x0000010100000101,
    0x0000010100010000, 0x0000010100010001, 0x0000010100010100, 0x0000010100010101,
    0x0000010101000000, 0x0000010101000001, 0x0000010101000100, 0x0000010101000101,
    0x0000010101010000, 0x0000010101010001, 0x0000010101010100, 0x0000010101010101,
    0x0001000000000000, 0x0001000000000001, 0x0001000000000100, 0x0001000000000101,
    0x0001000000010000, 0x0001000000010001, 0x0001000000010100, 0x0001000000010101,
    0x0001000001000000, 0x0001000001000001, 0x0001000001000100, 0x0001000001000101,
    0x0001000001010000, 0x0001000001010001, 0x0001000001010100, 0x0001000001010101,
    0x0001000100000000, 0x0001000100000001, 0x0001000100000100, 0x0001000100000101,
    0x0001000100010000, 0x0001000100010001, 0x0001000100010100, 0x0001000100010101,
    0x0001000101000000, 0x0001000101000001, 0x0001000101000100, 0x0001000101000101,
    0x0001000101010000, 0x0001000101010001, 0x0001000101010100, 0x0001000101010101,
    0x0001010000000000, 0x0001010000000001, 0x0001010000000100, 0x0001010000000101,
    0x0001010000010000, 0x0001010000010001, 0x0001010000010100, 0x0001010000010101,
    0x0001010001000000, 0x0001010001000001, 0x0001010001000100, 0x0001010001000101,
    0x0001010001010000, 0x0001010001010001, 0x0001010001010100, 0x0001010001010101,
    0x0001010100000000, 0x0001010100000001, 0x0001010100000100, 0x0001010100000101,
    0x0001010100010000, 0x0001010100010001, 0x0001010100010100, 0x0001010100010101,
    0x0001010101000000, 0x0001010101000001, 0x0001010101000100, 0x0001010101000101,
    0x0001010101010000, 0x0001010101010001, 0x0001010101010100, 0x0001010101010101,
    0x0100000000000000, 0x0100000000000001, 0x0100000000000100, 0x0100000000000101,
    0x0100000000010000, 0x0100000000010001, 0x0100000000010100, 0x0100000000010101,
    0x0100000001000000, 0x0100000001000001, 0x0100000001000100, 0x0100000001000101,
    0x0100000001010000, 0x0100000001010001, 0x0100000001010100, 0x0100000001010101,
    0x0100000100000000, 0x0100000100000001, 0x0100000100000100, 0x0100000100000101,
    0x0100000100010000, 0x0100000100010001, 0x0100000100010100, 0x0100000100010101,
    0x0100000101000000, 0x0100000101000001, 0x0100000101000100, 0x0100000101000101,
    0x0100000101010000, 0x0100000101010001, 0x0100000101010100, 0x0100000101010101,
    0x0100010000000000, 0x0100010000000001, 0x0100010000000100, 0x0100010000000101,
    0x0100010000010000, 0x0100010000010001, 0x0100010000010100, 0x0100010000010101,
    0x0100010001000000, 0x0100010001000001, 0x0100010001000100, 0x0100010001000101,
    0x0100010001010000, 0x0100010001010001, 0x0100010001010100, 0x0100010001010101,
    0x0100010100000000, 0x0100010100000001, 0x0100010100000100, 0x0100010100000101,
    0x0100010100010000, 0x0100010100010001, 0x0100010100010100, 0x0100010100010101,
    0x0100010101000000, 0x0100010101000001, 0x0100010101000100, 0x0100010101000101,
    0x0100010101010000, 0x0100010101010001, 0x0100010101010100, 0x0100010101010101,
    0x0101000000000000, 0x0101000000000001, 0x0101000000000100, 0x0101000000000101,
    0x0101000000010000, 0x0101000000010001, 0x0101000000010100, 0x0101000000010101,
    0x0101000001000000, 0x0101000001000001, 0x0101000001000100, 0x0101000001000101,
    0x0101000001010000, 0x0101000001010001, 0x0101000001010100, 0x0101000001010101,
    0x0101000100000000, 0x0101000100000001, 0x0101000100000100, 0x0101000100000101,
    0x0101000100010000, 0x0101000100010001, 0x0101000100010100, 0x0101000100010101,
    0x0101000101000000, 0x0101000101000001, 0x0101000101000100, 0x0101000101000101,
    0x0101000101010000, 0x0101000101010001, 0x0101000101010100, 0x0101000101010101,
    0x0101010000000000, 0x0101010000000001, 0x0101010000000100, 0x0101010000000101,
    0x0101010000010000, 0x0101010000010001, 0x0101010000010100, 0x0101010000010101,
    0x0101010001000000, 0x0101010001000001, 0x0101010001000100, 0x0101010001000101,
    0x0101010001010000, 0x0101010001010001, 0x0101010001010100, 0x0101010001010101,
    0x0101010100000000, 0x0101010100000001, 0x0101010100000100, 0x0101010100000101,
    0x0101010100010000, 0x0101010100010001, 0x0101010100010100, 0x0101010100010101,
    0x0101010101000000, 0x0101010101000001, 0x0101010101000100, 0x0101010101000101,
    0x0101010101010000, 0x0101010101010001, 0x0101010101010100, 0x0101010101010101
};

inline const uint64_t & unpack_byte(uint8_t x) {
    return unpacked_bytes[x];
}
```(I hand-coded the lookup table, by the way; it took a couple minutes with visual-block mode in gvim.) To compile that, I think you'll need to use g++ -std=c++0x (and probably #include <cstdint>).

---

### Post by LKjell on 2010-03-24
Lux Perpetua, amazing...

---

### Post by dwhitney67 on 2010-03-24
> **Lux Perpetua said:**
> I like this idea. All you need is a 1k lookup table.

You're kidding right??

I think the "Captain" already provided a simple solution; whether one does it in C or assembly, conceptually something similar to the following could be used:
```

#include <stdint.h>
#include <stdio.h>

int main(void)
{
   const uint8_t theByte = 0x69;    // 01101001
   uint64_t      result  = 0;
   uint8_t*      pResult = (uint8_t*) &result;

   for (size_t i = 0; i < 8; ++i)
   {
      *pResult++ = ((theByte >> i) & 1);
   }

   printf("Result: %016llx\n", result);

   return 0;
}

```

P.S.  I am not aware of any C library function/utility that permits one to display results in binary.  If the OP wants such, it would not take much thought on how to implement it.  The logic would be very similar to what is shown above.

---

### Post by NathanB on 2010-03-24
There exist an entire array of algorithms for packing/unpacking bit strings.  See this 'Art of Assembly' chapter for the details:  [http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/www.artofasm.com/Windows/HTML/BitManipulation.html#998259](http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/www.artofasm.com/Windows/HTML/BitManipulation.html#998259)

However, I suspect for your needs, you can get by with just using the obsolete Binary Coded Decimal (BCD) instructions.  Pretty nifty how just a few instructions perform such a mighty task:  [http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/www.artofasm.com/Windows/HTML/AdvancedArithmetica6.html#1007617](http://homepage.mac.com/randyhyde/webster.cs.ucr.edu/www.artofasm.com/Windows/HTML/AdvancedArithmetica6.html#1007617)

Nathan.

---

### Post by Lux Perpetua on 2010-03-25
> **dwhitney67 said:**
> You're kidding right??No, I wasn't. Obviously, there are pros and cons. If speed is the main concern, then mine is pretty viable (it seems to be 8-12 times faster than yours on my 32-bit laptop). On the other hand, if memory use is more important, then it's probably DOA. 

> **dwhitney67 said:**
> P.S.  I am not aware of any C library function/utility that permits one to display results in binary.  If the OP wants such, it would not take much thought on how to implement it.  The logic would be very similar to what is shown above.I did implement it a long time ago, but I have a feeling you wouldn't like it. (You can probably guess what it looks like! :-D)

---

### Post by MadCow108 on 2010-03-25
> **dwhitney67 said:**
> You're kidding right??

I think the "Captain" already provided a simple solution; whether one does it in C or assembly, conceptually something similar to the following could be used:

op does not seem to look for a simple solution, as the one he posted was already the second simplest, (if you throw out a few of the unnecessary shifts) but for a fast one

It would be more interesting to test the lookup table approach against the modified op's version, maybe I'll find some time later on.
probably one can also do something with this here:
[http://graphics.stanford.edu/~seander/bithacks.html#CountBitsSetParallelbithacks.html#CountBitsSetParallel](http://graphics.stanford.edu/~seander/bithacks.html#CountBitsSetParallelbithacks.html#CountBitsSetParallel)
I think you just need to modify the magic bits a little

---

### Post by CptPicard on 2010-03-25
Should have clarified that I assumed a 64 bit register ofc, but that should be obvious ;) In that case, I am at actually very surprised indeed that a lookup table doesn't just get bogged down by the memory access in comparison to just staying within registers...

---

### Post by Emill on 2010-03-25
I did some benchmarking. The lookup-version is way faster than the one that shifts bits. About the same speed as just using constant numbers.
I used this code:

```
int main(int argc, char *argv[]){
	uint64_t result[109];
	for(int i=0; i<2000000000; i++){
		int index = rand()%100;
		result[index] = unpack(i);
		result[index+1] = unpack(i);
		result[index+2] = unpack(i);
		result[index+3] = unpack(i);
		result[index+4] = unpack(i);
		result[index+5] = unpack(i);
		result[index+6] = unpack(i);
		result[index+7] = unpack(i);
		result[index+8] = unpack(i);
	}
	printf("%lld\n", result[3]);
}
```
26 secs for just assigning i, 26 secs for unpack_byte() lookup-table, 30 secs for my code.

If there are no assembly instruction that does this, I think I will use the lookup-version. But of course it is impossible backwards. So what is the fastest C/assembly code "packing" it?

---

### Post by lisati on 2010-03-25
> **CptPicard said:**
> What's wrong with simply always extracting the most significant bit of your 8bit number, ORing that with your 64bit number and then shifting that left by 8 and the 8bit number by one, repeating 8 times? Should fit into a very tiny asm loop.

Exactly. Doing something like this was my thought when I first noticed the original post in the thread.

---

### Post by MadCow108 on 2010-03-25
edit error in reasoning

---

### Post by Lux Perpetua on 2010-03-25
> **Emill said:**
> If there are no assembly instruction that does this, I think I will use the lookup-version. But of course it is impossible backwards. So what is the fastest C/assembly code "packing" it?If you can assume that the 64-bit input is properly formatted (i. e., that only the LSB of each byte is nonzero), then perhaps something like:

```
uint8_t pack(uint64_t y) {
    y += y>>7;
    y += y>>14;
    y += y>>28;

    return y;
}
```

**Edit**

For that matter, you can use a similar trick for the "unpack" operation:

```
uint64_t unpack(uint8_t x) {
    uint64_t y = x;
    y = (y&0xf) + ((y&0xf0)<<28);
    y = (y&0x300000003) + ((y&0xc0000000c)<<14);
    y = (y&0x1000100010001) + ((y&0x2000200020002)<<7);

    return y;
}
```I find that to be faster than the simple solutions of CptPicard & dwhitney67 on a 64-bit computer, but slower on my 32-bit laptop. That makes sense, since it depends more heavily on 64-bit arithmetic. (The lookup table is always faster.)

---

### Post by LKjell on 2010-03-26
When you calculate the speed is it including the table look up making or just the look up?

---

### Post by Npl on 2010-03-26
> **Emill said:**
> If there are no assembly instruction that does this, I think I will use the lookup-version. But of course it is impossible backwards. So what is the fastest C/assembly code "packing" it?
IF you got sse instructions pmovmskb does exactly that. wit gcc you could use it from within C code like this (dint test it):

```
int64 val;
val = val << 7; // shift LSB to MSB
int pack = __builtin_ia32_pmovmskb(*(*v8qi)&val ); // extract MSB of each byte
```

---

### Post by Emill on 2010-04-13
Thanks!
That was exactly what I was looking for. (Although I had to change that line a bit.. Now it works).
Just a single line of assembly code :)

---

### Post by Cracauer on 2010-04-14
What's the objective here, anyway?

From a pure instruction speed standpoint, CPUs of Netburst or newer generations will never be fast with bit-fiddling like this.

This packing would have to lead to very important space-savings to lead to an overall speedup.

---

