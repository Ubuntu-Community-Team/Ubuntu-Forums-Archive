---
title: "shift (bitshift) through char array"
date: 2008-08-29
forum: Programming Talk
---

### Post by monkeyking on 2008-08-29
Hi,
given a char(8bit's), I wan't get the value of every 2bits,
so that a char will contain 4 values.
This is easily done with a shift left command (<<2).

As far as I understand,
char arrays are simply the different chars in consecutive order in the memory.
so essentially, I should be able to just shift2, through the entire array.

But I can't make it work.

thanks in advance

[PHP]
int main(int argc, char *arg[]){
  unsigned char *chr = new unsigned char[8];
  for(int i=0;i<8;i++)
    chr[i] = 0x80 ;
  
  int i=0;
  unsigned char tmp;
  while((tmp=chr[i] )!= '\0'){
    printf("11xx-xxxx bits of chr[%d]=%x\n",i,tmp&0xc0); //extract 1100 0000
    tmp = tmp<<2;
    printf("xx11-xxxx bits of chr[%d]=%x\n",i,tmp&0xc0); //extract 0011 0000
    tmp = tmp<<2;
    printf("xxxx-11xx bits of chr[%d]=%x\n",i,tmp&0xc0); //extract 0011 0000
    tmp = tmp<<2;
    printf("xx11-xx11 bits of chr[%d]=%x\n",i,tmp&0xc0); //extract 0011 0000
    i++;
  }
  


[/PHP]

---

### Post by kpatz on 2008-08-29
Your code is working for me (after I add #include <stdio.h> at the top and the closing bracket at the bottom.)

You're loading each char with 0x80, so the output for each element in the array will be 0x80, 0x00, 0x00, 0x00 like it is producing.  0x80 = 10000000, so when you shift left by 2, you end up with 00000000 because the two leftmost bits get shifted off the end.  Thus the remaining 3 shifts return 00 as well.

Here's a version that is slightly different.  I shift the bits right instead of left, and pull the two lowest-order bits instead of the two highest-order bits.  This just makes the output more understandable.  If you want to continue shifting left and pulling the high-order bits, shift the result >>6 so the end result is 0,1,2,3 instead of 00,40,80,C0.   I also put more interesting values in the array instead of 0x80 in every position, so you can see how it works.

I fixed one other bug.  You were checking for the end of the array by looking for a value of zero, but didn't initialize the array with a zero at the end.  I did in my version.
[php]
int main(int argc, char *arg[]){
  // I put more interesting values in the array
  // This version shifts to the right instead of the left, and gets the
  // lowest order bits, which makes the results more useful without having
  // to shift the results 6 bits to the right
  unsigned char chr[] = { 0x12, 0x34, 0x56, 0x78, 0x9a, 0xbc, 0xde, 0xf0, 0 };
  int i=0;
  unsigned char tmp;
  while((tmp=chr[i] )!= '\0'){
    printf("1111-1111 bits of chr[%d]=%x\n",i,tmp);      // show whole thing
    printf("xxxx-xx11 bits of chr[%d]=%x\n",i,tmp&0x03); //extract 0000 0011
    tmp >>=2;
    printf("xxxx-11xx bits of chr[%d]=%x\n",i,tmp&0x03); //extract 0000 1100
    tmp >>=2;
    printf("xx11-xxxx bits of chr[%d]=%x\n",i,tmp&0x03); //extract 0011 0000
    tmp >>=2;
    printf("11xx-xxxx bits of chr[%d]=%x\n",i,tmp&0x03); //extract 1100 0000
    i++;
  }
}
[/php]

---

### Post by monkeyking on 2008-08-29
Ahh thanks for the revision,
i would have tracked these down for hours.

But maybe I wasn't clear enough.
In this version I have, I shift by 2, 4 times for each char.

I was looking for a more simplistic approach, 
where i just shift by 2 through the entire char array.
like the given pseudocode below.

[PHP]
while(chararray not empty){
  print first 2 bit.
  shift chararray by 2.
}
[/PHP]

but thanks again

---

### Post by kpatz on 2008-08-29
> **monkeyking said:**
> I was looking for a more simplistic approach, 
where i just shift by 2 through the entire char array.
like the given pseudocode below.The shift operator works only on a single item, so a single char, int, long, etc.  You could use unsigned long long, which is 64 bits, so you could fit 32 of your 2-bit values in it, and shift them all at once.

Your example code had an 8-byte array, so if that's the amount of data you're talking about, the unsigned long long would hold your data in a single value, no array required.

---

### Post by monkeyking on 2008-08-29
> **kpatz said:**
> The shift operator works only on a single item, so a single char, int, long, etc. 

Hmm, this is what I was afraid of. I need to store data in the magnitude of thousands. So I'll be stickinging with my chararray
But thanks.

---

### Post by dwhitney67 on 2008-08-29
Here's another spin on a solution:
[PHP]#include <stdint.h>
#include <iostream>
#include <iomanip>


int main()
{
  uint8_t values[8] = { 0xDE, 0xAD, 0xBE, 0xEF, 0xCA, 0xFE, 0xBA, 0xBE };

  // for each value in 'values'
  for ( size_t i = 0; i < 8; ++i )
  {
    // print the most-significant half-nibble first, least-significant last
    for ( int shift = 6; shift >= 0; shift-=2 )
    {
      std::cout << "["
                << std::setw(2) << std::setfill('0') << std::hex
                << ((values[i] >> shift) & 0x3)
                << "] ";
    }
    std::cout << std::endl;
  }

  return 0;
}[/PHP]

---

