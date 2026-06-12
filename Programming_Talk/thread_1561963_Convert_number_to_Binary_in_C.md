---
title: "Convert number to Binary? in C"
date: 2010-08-26
forum: Programming Talk
---

### Post by Kdar on 2010-08-26
How can I convert decimal number to Binary?

I was thinking to use  number%2 and get remainder. But how can I store all the remainders as a number? Array? Maybe it is a wrong way of doing it.

Can someone give me some advice?

---

### Post by worksofcraft on 2010-08-27
I think you can simply specify a binary format when printing...

something like:

printf("decimal %d = binary %b\n", number, number);

---

### Post by Kdar on 2010-08-27
oh let me try this.

---

### Post by schauerlich on 2010-08-27
> **worksofcraft said:**
> I think you can simply specify a binary format when printing...

something like:

printf("decimal %d = binary %b\n", number, number);

%b is not standard.

---

### Post by smartbei on 2010-08-27
The number is already stored in a binary format. If you want to access a particular bit, you can do so using bitwise operators:
```

unsigned int value;
unsigned int result;
// Get the Lowest bit:
result = value & 1;

// Get the Highest bit:
result = value >> (sizeof(unsigned int) - 1);

// Get the nth bit (LSB is 0):
result = (value >> n) & 1

```

---

### Post by Misiunio on 2010-08-27
For what purpose you want to convert? to display? or to perform some actions on certain bits?

---

### Post by Compyx on 2010-08-27
> **smartbei said:**
> The number is already stored in a binary format. If you want to access a particular bit, you can do so using bitwise operators:
```

unsigned int value;
unsigned int result;
// Get the Lowest bit:
result = value & 1;

// Get the Highest bit:
result = value >> (sizeof(unsigned int) - 1);

// Get the nth bit (LSB is 0):
result = (value >> n) & 1

```

Your 'highest bit' code doesn't do what you meant it to do; you left out CHAR_BIT:
```

result = value >> (sizeof(unsigned int) * CHAR_BIT - 1);

```

The sizeof operator yields the size of its operand in bytes, (C-bytes that is, which aren't always 8 bits wide). To get the number of bits, you need to multiply with CHAR_BIT, which holds the number of bits in a char.

Cheers.

---

### Post by WitchCraft on 2010-08-27
Bitshift might rely on endianness...

Try something like this:

Compile with:
```

gcc file.c -o mynumber.i386 -lm

```

```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <string.h>



int main(int argc, char* argv[])
{
   int sizeofNumber = (int) (log( (double) iNumber )/log(2.0)) + 1;

   char* mynumber = (char*) malloc(sizeofNumber + 1);
   memset(mynumber,0, sizeofNumber*sizeof(char));

   int i = 0;
   while(iNumber != 0)
   {
      int iDigit = iNumber %2;
      iNumber = iNumber /2 ;
      if(iDigit == 1)
         mynumber[sizeofNumber - i] = (char) itoa(iDigit);
      ++i;
   }


   mynumber[sizeofNumber (+1?)] = '\0'

   printf("%s\n", mynumber);

   return EXIT_FAILURE; // ;-)))
}

```
(Note: Above code is most certainly wrong.)



Should do this:
Decimal: 99'999
Binary : 11000011010011111

initial AboveValue = 99'999 = iNumber

=(int)(AboveValue/2) , LeftValue % 2
------------------------------
99999	1
49999	1
24999	1
12499	1
06249	1
03124	0
01562	0
00781	1
00390	0
00195	1
00097	1
00048	0
00024	0
00012	0
00006	0
00003	1
00001	1
00000	0

---

### Post by smartbei on 2010-08-27
Bit shifting does not rely on an architecture's endianity. In fact, a good compiler will optimize var/2 to the same assembly as var>>1 because it is faster.

Endianity has to do with how data is stored in memory. When operating on specific variables you can ignore it entirely.

@Compyx - thanks for correcting :-)

---

### Post by Kdar on 2010-08-27
> **Misiunio said:**
> For what purpose you want to convert? to display? or to perform some actions on certain bits?

get it to print would be nice. But I also want to add or subtract them in binary format

---

### Post by dwhitney67 on 2010-08-27
> **Kdar said:**
> get it to print would be nice. But I also want to add or subtract them in binary format

All numbers on your personal computer are stored as binary.  There is no such thing as base-10 numbers other than what you may print to the screen, save to a file, or write on paper.

There are no tools for displaying values in binary-format to the screen; you will need to develop this yourself.  Don't worry -- it's not rocket science level stuff.

---

### Post by pbrane on 2010-08-27
Here is one way to convert 32-bit integers to binary for display:
```

void binsprintf(char *s, int val)
{
  char *p;
  unsigned int t;
  p = s;
  t = 0x80000000;  // scan 32 bits
  for ( ; t > 0; t = t >> 1) {
    if (val & t)
      *p++ = '1';
    else
      *p++ = '0';
  }
  *p = 0;
}

```

---

### Post by WitchCraft on 2010-08-28
> **pbrane said:**
> deleted

Yehaa, now it works ;-)))


```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <string.h>


int main(int argc, char* argv[])
{
   int iNumber = -99999;
   char cSign = '+';

   if(iNumber < 0) 
   {
       cSign = '-';
       iNumber*=-1;
   }

   size_t uiNumberSize = (unsigned int) (log( (double) iNumber )/log(2.0)) + 1;
   ++uiNumberSize; // Sign

   char* szNumber = (char*) malloc(uiNumberSize + 1);
   memset(szNumber,'0', uiNumberSize * sizeof(char));
   
   int i = 1;
   for(; iNumber != 0; ++i)
   {
      int iDigit = iNumber % 2;
      iNumber = iNumber / 2 ;
      if(iDigit)
        szNumber[uiNumberSize - i] = '1';
   }
   
   szNumber[0] = cSign;

   
   szNumber[uiNumberSize] = '\0';
   printf("%s\n", szNumber);
   free(szNumber); // I forgot. No leaking please

   return EXIT_SUCCESS;
}

```

---

### Post by dwhitney67 on 2010-08-28
I've never seen a negative binary number represented with a minus sign.  Where did you get this notion from?

A signed-int value uses the most-significant bit to denote the sign of the value: 0 for positive numbers, and 1 for negative numbers.

And what is the purpose of the following (which I do not think it yields the value you seek):
```

   size_t uiNumberSize = (unsigned int) (log( (double) iNumber )/log(2.0)) + 1;
   ++uiNumberSize; // Sign

```
A byte occupies 8-bits on every system I have ever dealt with; probably the same will apply to you too.  Thus the number of characters necessary to store a 4-byte signed-int value in "binary format" will be 32 bytes (plus an additional byte if you wish to form a string).  This should suffice:
```

   size_t uiNumberSize = sizeof(int) * 8 + 1;

```
Lastly, for a mere 32 (or 33) bytes, you are wasting your time allocating the memory.  Just declare the value on the stack.


P.S.  Hungarian Notation... yuck!  :shock:

---

### Post by trent.josephsen on 2010-08-28
You don't need to depend on the assumption that a byte is an octet.  Use CHAR_BIT instead of 8.

---

### Post by dwhitney67 on 2010-08-28
> **trent.josephsen said:**
> You don't need to depend on the assumption that a byte is an octet.  Use CHAR_BIT instead of 8.

Or just use the macro _TYPEBITS(), if you are so inclined.

---

### Post by WitchCraft on 2010-08-28
> **dwhitney67 said:**
> 
I've never seen a negative binary number represented with a minus sign.  Where did you get this notion from?

Because I print it, since printed text is read by humans, and not computers.
I assume that anybody is intelligent enough to see that they need to fill the rest up with zero's if they want a 32 bit representation (including adding the MSB).

Instead of iNumber *= -1 you can also do a
iNumber = (~(iNumber-1));
which looks more professional ;-))


> **dwhitney67 said:**
> 
And what is the purpose of the following (which I do not think it yields the value you seek):
```

   size_t uiNumberSize = (unsigned int) (log( (double) iNumber )/log(2.0)) + 1;
   ++uiNumberSize; // Sign

```

It yields the minimum number of chars necessary to convert the binary representation into characters, omitting unnecessary leading zeros.


> **dwhitney67 said:**
> 
P.S.  Hungarian Notation... yuck!  :shock:

I know. 
But not using it sucks even more when anybody else but you needs to read your code.
For example, if anybody passes a string parameter, you see right away whether it is unicode or not.
Or when anybody uses a number, you see faster whether it is a float or a double.
Or it remembers you that integer division is not necessarely the correct result for your division computation.
Or it makes you think about it when someone for example puts a pointer into an int.
Because when you do use hungarian notation, you will realize right-away that on 64-Bit system, you'll need a long. 
If you don't, you'll realize it when your code strangely fails sometimes on a 64-Bit system. And when you realize it, you will have to change the entire program.
That is not very good when you're program is moderately complex, since 32 bit support will be phased out slowly but steadily.

---

### Post by trent.josephsen on 2010-08-28
> **dwhitney67 said:**
> Or just use the macro _TYPEBITS(), if you are so inclined.
Non-standard, I believe.

---

### Post by maximinus_uk on 2010-08-29
> **WitchCraft said:**
> Instead of iNumber *= -1 you can also do a
iNumber = (~(iNumber-1));
which looks more professional ;-))

If by "looks more professional" you mean "intent not immediately obvious" then you are right. To me the first one is much better - I can instantly grok what the programmer is doing.

And please - no more Hungarian notion; the compiler normally checks types nowadays, IDE's can give you this info and we have richer types anyway.

---

### Post by jpkotta on 2010-08-29
I just want to point out that there is *no such thing as a binary number*.  Binary vs. decimal vs. hexadecimal vs. English are all equally valid ways of *representing* an abstract number.  

```
1234 = 0x4d2 = 0b10011010010 = "one thousand two hundred thirty four"
```

In everyday usage, number and representation are often used in the same way without ambiguity, but when the distinction is necessary, in my experience, people become confused.

---

### Post by WitchCraft on 2010-09-04
> **jpkotta said:**
> 
but when the distinction is necessary, in my experience, people become confused.


But this distinction is necessary sometimes.
Or how else would you want to explain bitshifting / unary operations.
Stupidity is no excuse.

---

### Post by trent.josephsen on 2010-09-04
> **WitchCraft said:**
> But this distinction is necessary sometimes.
Or how else would you want to explain bitshifting / unary operations.
Stupidity is no excuse.
The only unary operators in C are (consults K&R) ! ~ ++ -- + - * & (type) and sizeof.  Only ~ operates on a number's representation.  Perhaps you meant the bitwise operators (& ^ | ~).

---

