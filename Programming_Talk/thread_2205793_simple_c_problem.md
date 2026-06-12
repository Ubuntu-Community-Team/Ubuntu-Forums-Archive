---
title: "simple c problem"
date: 2014-02-15
forum: Programming Talk
---

### Post by fugu2 on 2014-02-15
I need a little c help here:
how do I go about fixing this?
```

unsigned char array[] = "\x00\x01\x02\x03\x04\x05\x06\x07\x08\x09\x0A\x0B\x0C\x0D\x0E\x0F";
unsigned long number = 0x16171819;
memcpy(array, number, 4); //???
//looking for a result of "\x00\x01\x02\x03\x04\x05\x16\x17\x18\x19\x0A\x0B\x0C\x0D\x0E\x0F"

```

---

### Post by ofnuts on 2014-02-16
What you want to do isn"t very clear.... Plenty of problems:
- your array is 17bytes (you give 16 characters, plus ending \0)
- Your number is 8 bytes
- Why memcpy only 4 bytes (or why insist that the number should be a long when and int is enough)?
- This is likely to fail because you don't take in account the [endianness]("http://en.wikipedia.org/wiki/Endianness") of your processor:

---

### Post by fugu2 on 2014-02-16
Ok, thank you for you help with this,for me an unsigned long is only 4 bytes, running 32-bit,and so the number variable is only 4 bytes long.basically I would like to know of a way to use memcpy to write the 4 bytes in the unsigned long, into the unsigned char array at an arbitrarypoint in the array. I want to replace the bytes in the array, and notmake a new variable if thats possible.There can be a \x00 at the end of the array or not, I just want to knowthe proper syntax for memcpy because Im not that familiar programming in C.And as for endianess, for this example i dont care if the byte order is backwards.fyi, man memcpy has not helped me in this case.I'm thinking its suspose to be something like:

---

### Post by fugu2 on 2014-02-16
```

#include 
#include 
int main(){
	int i;
	unsigned char array[] = "\x00\x01\x02\x03\x04\x05\x06\x07\x08\x09\x0A\x0B\x0C\x0D\x0E\x0F";
	unsigned long number = 0x16171819;
	memcpy(&array+6, &number, 4);
	for(i=0; i<16; i++){
		printf("%02x", array[i]);
	}
	printf("\n");
	return 0;
}
```
But this just yeilds
```

000102030405060708090a0b0c0d0e0f

```
Any Ideas on how to fix this?

---

### Post by Bachstelze on 2014-02-16
*array* and *&array* are not the same thing. (This is subtle, on a common system they have the same value, but not the same type.) You want *array+6* and not *&array+6*.

---

### Post by trent.josephsen on 2014-02-16
To start with, if you need a 32-bit integer, #include <stdint.h> and use uint32_t, period. Never rely on short, int, long, etc. being any particular number of bits or bytes. The exception is char, which is always one byte by definition. (The number of bits in a byte is available through the macro CHAR_BIT, which is defined in limits.h.) By the same token, you should use "sizeof number" instead of 4 when calling memcpy.

Second, look at the memcpy invocation briefly. "array" is of type array[17]-of-unsigned-char. That means that "&array" is of type pointer-to-array[17]-of-unsigned-char. When you add 6 to that, you're telling the compiler to multiply 6 times the size of array-17-of-unsigned-char (e.g., 6*17 or 102), and then look at the address 102 bytes beyond the address "&array". Since your array is only 17 bytes in size, you're looking in no man's land and invoking undefined behavior.

What you want is the address of the seventh element of array: &array[6]. This is the same as (array + 6), but you can use whatever notation you like. 

(aside: There's an important reason I used "e.g." in the second paragraph above: this is an example, not a universal truth. I don't think you can assume that the difference between the pointers involved is exactly 102, although that assumption seems to hold true in my testing. Just understand the difference between array and &array.)

Here's how I would write your program. I made a couple smaller changes too.

```
#include <stdio.h>
#include <string.h>
#include <stdint.h>
int main(void)
{
	unsigned char array[] = "\x00\x01\x02\x03\x04\x05\x06\x07\x08\x09\x0A\x0B\x0C\x0D\x0E\x0F";
	uint32_t number = 0x16171819;
	memcpy(array + 6, &number, sizeof number);
	for(size_t i=0; i < sizeof array; i++){
		printf("%02x", array[i]);
	}
	putchar('\n');
	return 0;
}
```

Actually, I take that back. I wouldn't write this program, because I don't write C that relies on platform-specific assumptions about byte order. You shouldn't either. But if you *really* need to do this for some reason, the above is how you do it. If, instead, what you really need to do is store a 32-bit number in an array of 8-bit bytes, there are platform-agnostic ways to achieve that goal.

---

### Post by fugu2 on 2014-02-16
Okay thank you all very much.
memcpy(array + 6, &number, sizeof number); is a good enough anwser 
for me for right now, I'm still trying to understand addresses, pointers, 
casting and such. I don't plan to do much programming in C cause it 
causes too many headaches. I knew the anwser had to be something 
like this but I dont have enough experience yet to figure it out on my 
own.

---

### Post by Bachstelze on 2014-02-16
Looks like Trent woke up on the wrong side of bed this morning. :D What he said is true of course but you can feel free to disregard it for now and continue experimenting with pointers and stuff using good ol' numbers. What he said will not make any sense to you until you have grasped that anyway.

---

### Post by trent.josephsen on 2014-02-16
> **Bachstelze said:**
> Looks like Trent woke up on the wrong side of bed this morning. :D
Perceptive. :)

---

### Post by fugu2 on 2014-02-17
My initial soultion was to avoid memcpy like this,
```

#include 
#include 
#include 
int main(void)
{
	size_t i;
	unsigned char array[] = "\x00\x01\x02\x03\x04\x05\x06\x07\x08\x09\x0A\x0B\x0C\x0D\x0E\x0F";
	uint32_t number = 0x16171819;
	array[0x06] = (unsigned char)((number >> 24) & 0xff);
	array[0x07] = (unsigned char)((number >> 16) & 0xff);
	array[0x08] = (unsigned char)((number >> 8) & 0xff);
	array[0x09] = (unsigned char)(number & 0xff);
	for(i=0; i < sizeof array; i++){
		printf("%02x", array[i]);
	}
	putchar('\n');
	return 0;
}

```but that didnt help me understand how you can use memcpy, thank you all again

---

