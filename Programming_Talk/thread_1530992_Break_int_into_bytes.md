---
title: "Break int into bytes?"
date: 2010-07-14
forum: Programming Talk
---

### Post by xefix on 2010-07-14
Hi, all

I have an integer that is greater than or equal to 1 byte. I would like to break it into a byte array, but I'm not sure if there's a function that does this. 
If that doesn't make sense, imagine that I have the number 27389847, which is equivalent to 0x01A1EF97. I would like to have an array that looks like [0x01 0xA1 0xEF 0x97]. Please, point me in the right direction!

---

### Post by xefix on 2010-07-14
*headdesk* Sorry for the stupid question, I realized that this was simple math!

---

### Post by schauerlich on 2010-07-14
In case anyone's wondering, you can use a char pointer to get a byte at a time. You just need to watch for endianness.

---

### Post by slavik on 2010-07-14
> **schauerlich said:**
> In case anyone's wondering, you can use a char pointer to get a byte at a time. You just need to watch for endianness.
that and the other way is to do a shift and bitmask ...

in C:
```

typedef byte unsigned char;
byte bytes[8];
int myInt = 34567;
bytes[0] = myInt & 255;
bytes[1] = (myInt >> 8) & 255;
bytes[2] = (myInt >> 16) & 255;
... /* you get the point, can be done in a loop where bits shifted is index*8 */

```

Although char pointer is probably easier (since it is just access, minus the shifting).

---

### Post by nmaster on 2010-07-14
> **slavik said:**
> that and the other way is to do a shift and bitmask ...

in C:
```

typedef byte unsigned char;
byte bytes[8];
int myInt = 34567;
bytes[0] = myInt & 255;
bytes[1] = (myInt >> 8) & 255;
bytes[2] = (myInt >> 16) & 255;
... /* you get the point, can be done in a loop where bits shifted is index*8 */

```Although char pointer is probably easier (since it is just access, minus the shifting).

when i saw the title of the thread, my mind actually first jumped to the "mask and shift" idea.  using the char* is pretty smart though.

---

### Post by Sockerdrickan on 2010-07-14
I'd go with a char pointer personally

---

### Post by lisati on 2010-07-14
For some reason my mind jumped to "mod and shift" instead of the better "mask and shift". I think I need to get myself a fresh cup of coffee. :)

---

### Post by xefix on 2010-07-14
> In case anyone's wondering, you can use a char pointer to get a byte at a time. You just need to watch for endianness.

How would one do that, exactly? My solution, as I said before, involved simple mathematical operations, something like this:

```

int longInt = 1293819;
int byteArray[numbytes];
for(eachbyte){
   currentByte = longInt % 256;
   longInt = longInt / 256;
   byteArray[numbytes-1-i] = curByte; 
}

```

---

### Post by slavik on 2010-07-14
mod and integer division on x86 are the same operation (idiv), what happens is that one register gets the result of division (I forget the proper term for this) and the other gets the remainder, so the difference is what you read.

with that said, compared to other approaches, idiv is expensive (division/mutiplication are expansive, hence mmx/sse type additions to CPUs).

example of char pointer access.

```

typedef byte unsigned char;
byte *myByte;
int myInt = 3456789;
myByte = &myInt;
printf("%X\n", myByte[0]);
printf("%X\n", myByte[1]);

```

of course, mind the endianness as it will affect which bytes you get out of memory what byte the address points to.

---

### Post by xefix on 2010-07-14
@slavik

Wouldn't your code complain about pointer casting? (int* to unsigned char*)

Also, I guess the byte pointer isn't treating the integer as a char array, but why? I mean, it won't see your int as {'3', '4', '5'}, right?

---

### Post by schauerlich on 2010-07-14
> **xefix said:**
> @slavik

Wouldn't your code complain about pointer casting? (int* to unsigned char*)

Also, I guess the byte pointer isn't treating the integer as a char array, but why? I mean, it won't see your int as {'1', '3', '5'}, right?

It might be good practice to explicitly cast it, but I doubt GCC would complain (maybe with -Wall). int and char are basically just shortcuts to say "give me (4 or 1) bytes of memory, and interpret it as (signed or unsigned)". An int is stored as 4 bytes, and a char is 1 byte. It's all just 1's and 0's, there's nothing sacred about its type on a physical level. If you use a char pointer to point the area of memory where an int is stored, when you dereference it, it will give you one byte at a time, interpreted as unsigned.

Sorry, I didn't word that very well...

---

### Post by xefix on 2010-07-14
Oh, I understand. Thank you!

---

### Post by Tech2077 on 2010-07-14
I personally would have done the shift and mask, but char pointer never came to mind. :P

---

### Post by slavik on 2010-07-15
> **schauerlich said:**
> It might be good practice to explicitly cast it, but I doubt GCC would complain (maybe with -Wall). int and char are basically just shortcuts to say "give me (4 or 1) bytes of memory, and interpret it as (signed or unsigned)". An int is stored as 4 bytes, and a char is 1 byte. It's all just 1's and 0's, there's nothing sacred about its type on a physical level. If you use a char pointer to point the area of memory where an int is stored, when you dereference it, it will give you one byte at a time, interpreted as unsigned.

Sorry, I didn't word that very well...
1. explicit casting is "good for you" (tm). But I didn't, so I suck.
2. No, you won't individual integers, these are bytes we're grabbing ;)
3. Don't take "it's all 0s and 1s in the end" for granted. There was a time when this concept was a very new thing which gave us stored/resident programs. This also gave us programs that could modify themselves (LISP is the best example of this) and modify other programs (although protected mode and such on x86 prevents that). The other big thing was software interrupts, which eventually gave way to exceptions.

---

