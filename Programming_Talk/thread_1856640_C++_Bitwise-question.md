---
title: "C++ Bitwise-question"
date: 2011-10-08
forum: Programming Talk
---

### Post by DarkAmbient on 2011-10-08
hey, been banging my head for a few hours now. Trying to learn more about bitwise operations. 

The reason I'm curious about this is because of its speed. Loading and unloading alot of information in my app. And I need to use atleast 3 variables (1 short and 2 chars (all unsigned) is the "lowest" I can go) that will be loaded and "unloaded" from memory almost constantly. 

Is it possible to merge this short (2 bytes) and the 2 chars (a byte each) into an int (4 byte). Then write them to a binaryfile, to later read from the binaryfile and get the same values as before the merge?

My guess is no, but you never know. I still hasn't understood "bitwise-magic". If it's possible, perhaps it wouldn't increase speed after all?

---

### Post by Arndt on 2011-10-08
> **DarkAmbient said:**
> hey, been banging my head for a few hours now. Trying to learn more about bitwise operations. 

The reason I'm curious about this is because of its speed. Loading and unloading alot of information in my app. And I need to use atleast 3 variables (1 short and 2 chars (all unsigned) is the "lowest" I can go) that will be loaded and "unloaded" from memory almost constantly. 

Is it possible to merge this short (2 bytes) and the 2 chars (a byte each) into an int (4 byte). Then write them to a binaryfile, to later read from the binaryfile and get the same values as before the merge?

My guess is no, but you never know. I still hasn't understood "bitwise-magic". If it's possible, perhaps it wouldn't increase speed after all?

Of course you can pack one 2-byte and two 1-byte quantities into a 4-byte memory space, and then pass it around, write it to disk and read it back again.

But for the speed comparison, what are you comparing to? Writing the values in some kind of text form?

---

### Post by ofnuts on 2011-10-08
> **DarkAmbient said:**
> hey, been banging my head for a few hours now. Trying to learn more about bitwise operations. 

The reason I'm curious about this is because of its speed. Loading and unloading alot of information in my app. And I need to use atleast 3 variables (1 short and 2 chars (all unsigned) is the "lowest" I can go) that will be loaded and "unloaded" from memory almost constantly. 

Is it possible to merge this short (2 bytes) and the 2 chars (a byte each) into an int (4 byte). Then write them to a binaryfile, to later read from the binaryfile and get the same values as before the merge?

My guess is no, but you never know. I still hasn't understood "bitwise-magic". If it's possible, perhaps it wouldn't increase speed after all?

No need to use bitwise logic. When you need to look at storage in different ways, the "union" is your friend:
```

#include <stdio.h>

struct intMap {
    short theShort;
    char theChar;
    int theBits1:4;
    int theBits2:4;
};

union mappedInt {
    int theInt;
    struct intMap theIntMap;
};


int main(int argc, char **argv) {
    union mappedInt m;
    m.theInt=0x12345678;
    printf("Sizeof: int: %d, intMap: %d\n",sizeof m.theInt, sizeof m.theIntMap);
    printf("%04x/%02x/%1x/%1x\n",m.theIntMap.theShort,m.theIntMap.theChar,m.theIntMap.theBits1,m.theIntMap.theBits2);
    return 0;
}

```If you execute you get "5678/34/2/1" due to the endianness of the x86 architecture. Unions are often platform/architecture dependent. Note that the complete syntax of unions even allows bitstrings (ie, groups of bits withing a byte)

Code above is C but unions also exist in C++.

---

### Post by DarkAmbient on 2011-10-09
thanks for your replies. Might add that I had been coding way to long yesterday when I posted, so I wasn't really clear.

With speed-comparison I meant any way that is quite fast. ;) Earlier I used 3 int and for storing the info. Added them to an array, and fwrite in binary-format. Then fread to get the info again. Guess I could save each variable in diff. bit-length one at a time. But I'd prefer making only 1 call to fwrite on saving this info, and 1 to fread on load. 

Hadn't thought about unions. Never got the chance to try 'em myself actually, only read about them. Seems like a fitting way to solve my storing issue. :)

But from that example, what does this mean more exactly? (I'm not sure what to search on for reading about it)

```
		int theBits1:4;
		int theBits2:4;
```

Only use 4bits from the int?

---

### Post by ofnuts on 2011-10-09
> **DarkAmbient said:**
> thanks for your replies. Might add that I had been coding way to long yesterday when I posted, so I wasn't really clear.

With speed-comparison I meant any way that is quite fast. ;) Earlier I used 3 int and for storing the info. Added them to an array, and fwrite in binary-format. Then fread to get the info again. Guess I could save each variable in diff. bit-length one at a time. But I'd prefer making only 1 call to fwrite on saving this info, and 1 to fread on load. 

Hadn't thought about unions. Never got the chance to try 'em myself actually, only read about them. Seems like a fitting way to solve my storing issue. :)

But from that example, what does this mean more exactly? (I'm not sure what to search on for reading about it)

```
        int theBits1:4;
        int theBits2:4;
```Only use 4bits from the int?
Exactly... and if the bitstrings(*) are next to each other, they will be put in the same byte if they fit, so
```

union test {
  int fourbits:4;
  int threebits:3;
  int onebit:1;
} t;

```
defines something that fits in one byte (sizeof t==1). There are a couple of restrictions, like not be able to take the address or sizeof  of a bitstring, and again, depending on platform and usage you'll want to check the actual order (for instance if these are the contents of some control register in an I/O device).

(*) If you want to google for more, IIRC in C & C++  they use the term "bitfield" instead of "bitstring".

---

### Post by DarkAmbient on 2011-10-09
> **ofnuts said:**
> Exactly... and if the bitstrings(*) are next to each other, they will be put in the same byte if they fit, so
```

union test {
  int fourbits:4;
  int threebits:3;
  int onebit:1;
} t;

```
defines something that fits in one byte (sizeof t==1). There are a couple of restrictions, like not be able to take the address or sizeof  of a bitstring, and again, depending on platform and usage you'll want to check the actual order (for instance if these are the contents of some control register in an I/O device).

(*) If you want to google for more, IIRC in C & C++  they use the term "bitfield" instead of "bitstring".

Oh my science, this is great! Thanks a lot for clarifying. I will most definitely consider this as an solution to store me'bits. Thread solved I say.

---

### Post by akvino on 2011-10-12
Another way to do it is to use reinterpret cast:

[http://www.cplusplus.com/doc/tutorial/typecasting/](http://www.cplusplus.com/doc/tutorial/typecasting/)

Or to simplify in your example:

[PHP]
//declare variable you want to cast over what you're getting
//make sure that variables you're getting are stored sequentially 
//in memory

//if you don't like pointers you can store the value in uint
unsigned int  desiredValue = 0;

//reinterpret cast works with pointers and you can continue to 
//use pointers
unsigned int*  p_desiredValue = NULL;

//reinterpret cast
desiredValue = reinterpret_cast<unsigned int *>(&valueToConvert);

//store in non pointer form
desiredValue = *p_desiredValue; 


[/PHP]

---

