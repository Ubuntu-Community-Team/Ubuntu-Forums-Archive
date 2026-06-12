---
title: "Bitwise Operators"
date: 2006-12-30
forum: Programming Talk
---

### Post by welshboy on 2006-12-30
Hi Folks,

Hope you had a merry christmas, and that you're looking forwards to 2007.

I'm reading Ivor Horton's book on Java as a kind of refresher, but I'm wondering if there is any practical use for bitwise operations? 

I've read and re-read the section, and it isn't clear to me what use they may have. 

If anyone understands, would you be kind enough to explain it in simple terms?  and also give an example of what practical use it could have in programming?

Many thanks

---

### Post by gpolo on 2006-12-30
well, I have done things in C that needed to play with big-endian and little-endian and It was a lot easier to use bitwise operations to do the things I needed. But, java, c++ and other languages (C doesn't) take care of endianess. So.. all depends on what you will do in future

---

### Post by Wybiral on 2006-12-30
If you are talking about bitwise operators such as and, or, xor, left/right shift, etc... They do actually have practical uses from time to time. One example that comes to mind is this...

Most 3d graphics API's deal with textures of dimensions that are a power of two. Suppose you wanted to write a function to check the texture, or to list a certain number of "power of two's" using the left shift operator, it's very simple. Here is why...

000000000001 = 0001 = 1<<0
000000000010 = 0002 = 1<<1
000000000100 = 0004 = 1<<2
000000001000 = 0008 = 1<<3
000000010000 = 0016 = 1<<4
000000100000 = 0032 = 1<<5
000001000000 = 0064 = 1<<6
000010000000 = 0128 = 1<<7
000100000000 = 0256 = 1<<8
001000000000 = 0512 = 1<<9
010000000000 = 1024 = 1<<10
100000000000 = 2048 = 1<<11

Notice why it's called the left shift operator?

Here's an example of it's use in c++ (sorry, I'm not a java guy)...
```
#include <iostream>
using namespace std;

int main(){
	for(int x=0; x<12; x++)
		cout << (1<<x) << endl;
}
```

Which is much simpler and faster than using pow(2, x). So, any time you need a 2^x, you can just use 1<<x instead.

Some of their uses do much more interesting things, for instance if you use: (x & y) when rendering a picture (naturally for each pixel at x, y) you get a Sierpinski's triangle. Here's another c++ example of that...
```
#include <iostream>
using namespace std;

int main(){
	for(int y=0; y<32; y++){
		for(int x=0; x<32; x++){
			if(x&y) cout << "##";
			else cout << "  ";
		}
		cout << endl;
	}
}
```

Some other applications include: encryption algorithms, graphical manipulations for imaging programs, various math speed-boost tricks, psuedo-random number generators, and probably a lot more that I don't know of. Anyway, the point is that they do come in handy some times and it's worth giving them the time of day, you never know when they will help you solve a problem or reduce a solution.

---

### Post by slavik on 2006-12-30
when you shift left or right an integer, it is a VERY cheap multiplication/division operation.

shifts and xor are also used for encryption.

a way to switch 2 vars using xor:
a^=b;
b^=a;
a^=b;

look up the insqrt function from quake3 engine, what is neat about it is that it uses the Newton method for finding 1/sqrt(n), but what it does is convert a float into an int and then shift it to get an almost free division by 2.

also, in the 8086 CPU, 'mov ax, 0' to zero out ax is pretty inefficient (since the '0' has to be encoded), a faster way is 'sub ax,ax' or 'xor ax,ax'

---

### Post by pharcyde on 2006-12-30
Bitwise operations have a variety of uses primairly if you are writing device drivers.  Like it was said earlier using the shift instructions is much faster than using divide/multiply instructions.  But you can only do this substitution if the divide/multiply operation is a power of 2.  Other uses may include reversing the bits in a byte, combining the high and low part of 2 nibbles, etc.  Here is some code below.

reverse bits in a byte:
```

uint8_t my_byte = 0x0F;
uint8_t reverse_byte = 0x00;

for(uint8_t i = 0; i < 8; i++)
{
 reverse_byte |= my_byte & 0x1;
 reverse_byte << 1;
 my_byte >> 1;
}

```

combing 2 nibbles:
```

uint8_t nib1 = 0x0F;
uint8_t nib2 = 0x0F;
uint8_t byte = 0x00;

byte = nib1;
byte |= (nib2 << 4);

```

---

### Post by Ragazzo on 2006-12-30
> **slavik said:**
> when you shift left or right an integer, it is a VERY cheap multiplication/division operation.

The compiler should optimize such multiplications or divisions even if you don't use shift operations.

---

### Post by Grey on 2006-12-30
I use them ALL THE TIME.  I can't really think of any particular uses off the top of my head though.  I'll look through some of my code to try to find something, other than the obvious multiplication/division use listed above, or endianness.

**1) Passing flags to a function (OR operator).**

Sometimes, (often used in console hardware), flags are set as individual bits in a set memory location.  So, as an example, if you want to set up the screen to have 256 colors and a 256x256 bitmapped background, you might do something like this:

```

set_screen(COLOR_256 | BG_SIZE_256x256);

```

That way, the #defined flags use the bitwise or operator to setup a byte of data, very easily, and readably.

**2) Checking flags on a byte (AND operator). **

Oftentimes, status of keyboard buttons, or gamepad buttons will be returned as a single value, rather than an array.  This is for rather obvious performance reasons.  It's up to the programmer to extract individual bits from the number.  So, if you wanted to check if the player has pressed the "A" button, you might do something like this:

```

if(key_mask & A_BUTTON){
  //do something
}

```

**3) Checking bits in a byte. (AND and SHIFT)**

Sometimes, you will want to check each individual bit in a byte.  you can do that with something like this:

```

for(u16 i = 0; i < max_number; i++)
{
	if((0x01) & (bitmask >> i))
	{
		//do something
	}
	else
	{
		//the bit isn't set.
	}
}

```

**4) Extreme optimization.**

Here's a snippet of code from Quake 3.  It's completely unreadable.  But it's blazing fast, and does its job very well.  I have no idea how or why it works.  It just does.

```

float InvSqrt (float x){
   float xhalf = 0.5f*x;
   int i = *(int*)&x;
   i = 0x5f3759df - (i>>1);
   x = *(float*)&i;
   x = x*(1.5f - xhalf*x*x);
   return x;
}

```

---

### Post by UK-sHaDoW on 2006-12-31
Well in c , and Programming embedded systems, you can't go without them to set up outputs on ports and such. I suppose you could use bitfields too.
Its mainly getting the computer communicating with other hardware is where i use them.

Plus it can take advantage of the binary number system, as that fast invert square shows. I should point out its not completely accurate calculation but good enough(read about it on digg).

Most math stuff is automatically optimised by the compiler though.

---

