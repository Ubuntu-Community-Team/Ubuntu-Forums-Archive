---
title: "Union and Structure tricks in C."
date: 2009-01-22
forum: Programming Talk
---

### Post by Thesuperchang on 2009-01-22
Hi, I was hoping that some one could clarify if what I want to do in C is possible or not. Ok, I have two structures one union as seen below;
[PHP]typedef unsigned char reg8;
typedef unsigned short reg16;

typedef struct {
	reg8 C, B,
	     E, D,
	     L, H,
	     F, A;
} _Small;

typedef struct {
	reg16 BC,
	      DE,
	      HL,
	      PSW;
} _Large;

typdef union {
	_Large large;
	_Small small;
} _Registers[/PHP]

The idea is that the small and large values of the two structures are interlocked. However the problem here is the verbosity required to access either of the two structures members. I am seeking a way to access members as seen below, however the compiler whines if I try such a method as seen below;
[PHP]typedef unsigned char reg8;
typedef unsigned char reg16;

typedef union {
	typedef struct {
		reg8 C, B,
		     E, D,
		     L, H,
		     F, A;
	};
	typedef struct {
		reg16 BC,
		      DE,
              HL,
              PSW;
	};
} _Registers;[/PHP]

Is there any way this could be done without the intervention of pointers?

---

### Post by Xamiga on 2009-01-22
Long time since I coded.  The ';' after your first 'H' isn't correct????

---

### Post by mdurham on 2009-01-23
> **Xamiga said:**
> Long time since I coded.  The ';' after your first 'H' isn't correct????

Also after the A & PSW I believe.

---

### Post by slavik on 2009-01-23
after A and PSW is fine. but when you have a union of two anonymous structure, how do you refer to a specific structure in the union? ;)

---

### Post by Thesuperchang on 2009-01-23
In theory I was hoping to access the members like so;
[PHP]_Registers reg;
reg.C = 0x00;
reg.B = 0x00;

reg.DE = 0x0000;
[/PHP]

Altering the value reg.C and reg.B will also change the value of reg.BC. Likewise reg.DE will change reg.E and reg.D. I do not know if this sort of programming is valid in C or not, hence the reason I'm asking here.

The out of place ";" was a copy and paste mistake. They were always intended to be ",".

---

### Post by slavik on 2009-01-23
yea, not going to work :(

I also don't think that you can overlay access like this ... I am not sure though, also keep in mind that all your variables are all same size anyway. :)

---

### Post by eye208 on 2009-01-23
You probably want to define reg16 as unsigned short, not unsigned char.

If reg.small.C is too verbose, what about reg.s.C? Just rename the union members.

---

### Post by Cracauer on 2009-01-23
> **Thesuperchang said:**
>  I am seeking a way to access members as seen below, however the compiler whines if I try such a method as seen below;


Please don't say "the compiler whines" without posting the error messages.

> **Thesuperchang said:**
>  [PHP]typedef unsigned char reg8;
typedef unsigned char reg16;

typedef union {
	struct {
		reg8 C, B,
		     E, D,
		     L, H,
		     F, A;
	};
	typedef struct {
		reg16 BC,
		      DE,
              HL,
              PSW;
	};
} _Registers;[/PHP]

Is there any way this could be done without the intervention of pointers?

You just got typedef disease, that's all. In general this stuff works fine.

```

#include <stdio.h>
#include <arpa/inet.h>

typedef unsigned char reg8;
typedef unsigned short reg16;

int main(void)
{

  union {
    struct {
      reg8 C, B,
        E, D,
        L, H,
        F, A;
    } one;
    struct {
      reg16 BC,
        DE,
        HL,
        PSW;
    } two;
  } _Registers;  

  _Registers.one.C = 0xDE;
  _Registers.one.B = 0xAD;
  _Registers.one.E = 0xBE;
  _Registers.one.D = 0xEF;

  printf("%X %X\n", _Registers.two.BC, _Registers.two.DE);
  printf("%X %X\n", htons(_Registers.two.BC), htons(_Registers.two.DE));

  return 0;
}

```

gcc -o l l.c && ./l
ADDE EFBE
DEAD BEEF

Note that on x86 you have byte swap going on. This might or might not be what you want.

---

### Post by Thesuperchang on 2009-01-23
Alright, it's a pity that such a method cannot be accomplished in C. I suppose pointer are the way to go in this case.

In case anyone wanted to know, this idea arose when working on an Intel 8080 emulator. Specific 8bit registers could be combined to form 16bit registers. This projects source can be downloaded through the links below if anyone wants a look see.

[Core]("http://www.megaupload.com/?d=YQY01JMZ") -- Timing has not been implemented. Has not been debugged but seems to execute code correctly.
[Assembler]("http://www.megaupload.com/?d=UOVJ8ARC")
[Disassembler]("http://www.megaupload.com/?d=KI6FAGGM")

Thanks for clarifying,
C. Anderson

---

### Post by slavik on 2009-01-24
> **Thesuperchang said:**
> Alright, it's a pity that such a method cannot be accomplished in C. I suppose pointer are the way to go in this case.

In case anyone wanted to know, this idea arose when working on an Intel 8080 emulator. Specific 8bit registers could be combined to form 16bit registers. This projects source can be downloaded through the links below if anyone wants a look see.

[Core]("http://www.megaupload.com/?d=YQY01JMZ") -- Timing has not been implemented. Has not been debugged but seems to execute code correctly.
[Assembler]("http://www.megaupload.com/?d=UOVJ8ARC")
[Disassembler]("http://www.megaupload.com/?d=KI6FAGGM")

Thanks for clarifying,
C. Anderson
I figured that you were simulating  a CPU when you named 4 registers in double letters in one but spearated the single letters in the other struct.

Please don't simulate an 8080 ... x86 assembly is almost as bad as MIPs ... motorola 68000 series is much nicer, so is IBM's 370 (370 has 16 general purpose registers).

---

### Post by jpkotta on 2009-01-24
You should use the uint8_t and uint16_t types from stdint.h; they are guaranteed to be the correct size, unlike short and char.

> **slavik said:**
> Please don't simulate an 8080 ... x86 assembly is almost as bad as MIPs ... motorola 68000 series is much nicer, so is IBM's 370 (370 has 16 general purpose registers).

Agreed.

---

### Post by Cracauer on 2009-01-26
> **Thesuperchang said:**
> Alright, it's a pity that such a method cannot be accomplished in C. I suppose pointer are the way to go in this case.


Did I miss something? It works fine, see the code I gave you.

---

