---
title: "[SOLVED] [C++] and extended ASCII"
date: 2008-05-18
forum: Programming Talk
---

### Post by Can+~ on 2008-05-18
I have this homework, about the Huffman tree, in which you read a file, generate the frequency of each character, and build a tree with the less common characters deeper on the tree, and the most common characters on top.

That section is done. Everything works perfect and I could just send the homework, BUT! When reading the input file (which is UTF-8 by default), any other character than the normal ASCII set causes a segmentation fault. The homwork asked about the "Ascii characters between 32 and 255", but the problem is, I've been looking up and down on google for a straight tutorial on how print them.

I don't need to do anything with the characters, in fact, it already stores the ascii value between 32 and 255 of each character, and it just moves them from File A (plain text) to file B (another plain text, which is supposed to be binary, but we must leave it as plaintext so the guy who checks the homework can read it) and backwards.

So that's my question, I just need the extended ascii set, the harder part of the task is done (the huffman tree). Actually, I've never wandered outside the normal ASCII set, so I'm pretty newb with this things of character encoding.

Oh, and it's most likely it will be spanish (áéíóú...).

---

### Post by Can+~ on 2008-05-18
Ok, I finally fixed it. For some reason, certain characters between 127 and 255 were NEGATIVE (áéíóú, ñ, ...). After hours of debugging, I change everything to unsigned chars (but seriously, I thought that chars where unsigned by default).

This is the point I want to make a statement about C++, **IT SUCKS**. For instance, I had an array which holded the amount of repetitions of each character:

[PHP]int frequencies[256];[/PHP]

Now, when reading the file, for some reason, it readed some characters as negative, making the following thing:

[PHP]frequencies[-5]++;[/PHP]

It should have raised an error there, instead, it went to the memory, and replaced something it shouldn't, without even telling me. For some reason, the application kept running, until requesting the value in the position that was screwed up, therefore, causing a [FONT="Courier New"]segmentation fault[/FONT]. And segmentation fault little tells you where the error is. Instead I had to debug every single piece of code of my damn program to find that accents cause negative values, and that replaced memory.

It's ok. It was my fault to not find the error, but I'm not perfect. But it just didn't locked or avoided the replacement of a variable outside of the range of the array.

---

### Post by dwhitney67 on 2008-05-18
I wouldn't say that C++ (or C) sucks... perhaps it just needs semi-intelligent people to understand how to deal with it.

Anyhow, a char is a "signed" char, thus only holding 7-bits of data and a sign-bit.  Thus it can hold values -127 to 127 (or -0x7F to 0x7F).  The 8th bit is either a 0 (positive number) or 1 (negative number).

An unsigned char, which must explicitly be declared as such if one wants to use the 8th bit for storing data, can hold 8-bits.  Thus values from 0 - 255 (or 0x00 to 0xFF) can be stored.

If you need an unsigned char, int, or whatever... then declare it as such.  Don't mix types and then expect the application to figure out what you "intended" to occur.  Computers unfortunately are not that smart yet.

Also, remember that when you access an array using the [], you are in essence performing an arithmetic operation; that is, the index given is an offset from the array's initial address.  Thus the following statements are equivalent:
[PHP]
array[ -5 ] = 1;
*(array - 5) = 1;[/PHP]

Good luck with your next assignment.

---

### Post by Can+~ on 2008-05-18
> **dwhitney67 said:**
> <too big>

I agree, I screwed it up. I probably should've forseen the error, the problem came that I tested with simple text files on english. Later I tested with other characters on extended ascii. And I know that characters can overwrite their last bit, thus making it negative.

And I know how the pointers work inside an array. It just jumps [FONT="Courier New"]p = n*sizeof(type)[/FONT] inside the array in the space of memory, and with negative values, it jumped backwards (where p is a pointer of type [FONT="Courier New"]type[/FONT], [FONT="Courier New"]type[/FONT] is the type of the variable in question, and [FONT="Courier New"]n[/FONT] is the requested index.)

What I'm asking to C++, is that it could tell me about those idiocies, since I'm human. For instance, having a negative value inside an array should've been told by the compiler, instead I just got segmentation faults.

Maybe my writing is a little biased on the anger of the wasted time on this issue.

---

### Post by Bichromat on 2008-05-19
> **dwhitney67 said:**
> Anyhow, a char is a "signed" char, thus only holding 7-bits of data and a sign-bit.  Thus it can hold values -127 to 127 (or -0x7F to 0x7F).  The 8th bit is either a 0 (positive number) or 1 (negative number).

An unsigned char, which must explicitly be declared as such if one wants to use the 8th bit for storing data, can hold 8-bits.  Thus values from 0 - 255 (or 0x00 to 0xFF) can be stored.

A char holds 8 bits of data, signed or unsigned. What you describe here was true for some old architectures. This system has two values for zero. Nowadays, integers are stored using 2's complement arithmetic. Thus, a signed char can hold values from -2^8=-128 to 2^8-1=127.

---

### Post by JupiterV2 on 2008-05-19
> **dwhitney67 said:**
> 
Also, remember that when you access an array using the [], you are in essence performing an arithmetic operation; that is, the index given is an offset from the array's initial address.  Thus the following statements are equivalent:
[PHP]
array[ -5 ] = 1;
*(array - 5) = 1;[/PHP]

I feel stupid. I didn't know that you could dereference the array and use an arithmetic operation to access elements. Thanks.

---

### Post by johnl on 2008-05-19
You can have all sorts of fun with array access in C/C++!

```

#include <stdio.h>

int main(int argc, char* argv[]){

   // let's take the argv'th element of the array 0...
   printf("%s\n", 0[argv]);
   
   int i;
   for(i = 0; i < argc; ++i) {
      // and the argv'th element of the array i...
      printf("arv[%d] = %s\n", i, i[argv]);
   }     

}

```

---

