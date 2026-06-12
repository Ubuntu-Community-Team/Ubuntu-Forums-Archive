---
title: "Opcodes help"
date: 2008-08-04
forum: Programming Talk
---

### Post by loganwm on 2008-08-04
I'm just looking for a quick solution to this problem I have, I'm sure it's simple, but I can't seem to find out on my own.

I'm following a Chip-8 emulator programming tutorial a bit, I understand the opcodes, I understand how the system works, what the opcodes do, I just need to process them:

Each opcode is a 2-byte value, and my problem is the following example:

The JUMP command is 1NNN where NNN is an address.

I intend to use a switch case, but I don't know how to process an opcode with variable parts like the above?

NOTE: This is in C

---

### Post by dwhitney67 on 2008-08-04
If you are writing in C, use snprintf() to put together a string representing the "1NNN".  For example:
[PHP]int value NNN = 0x123;
char addrBuf[5] = {0};
snprintf( addrBuf, sizeof(addrBuf), "1%03x", NNN );[/PHP]

If you require an integer value, then you have two options:
[PHP]int addr = 0x1000 + NNN;
// or
int addrFromStr = strtol( addrBuf, 0, 16 );   // addrBuf being from the snprintf() above[/PHP]
I not quite certain you need to perform a switch(), unless I'm missing something.

---

### Post by Npl on 2008-08-04
> **loganwm said:**
> I'm just looking for a quick solution to this problem I have, I'm sure it's simple, but I can't seem to find out on my own.

I'm following a Chip-8 emulator programming tutorial a bit, I understand the opcodes, I understand how the system works, what the opcodes do, I just need to process them:

Each opcode is a 2-byte value, and my problem is the following example:

The JUMP command is 1NNN where NNN is an address.

I intend to use a switch case, but I don't know how to process an opcode with variable parts like the above?

NOTE: This is in C
Mask out the variable part.
```
unsigned int instr; // your instruction in native endianess
unsigned int address ;

// extract first byte
switch( (instr >> 12) & 0xF)
{
case 0:
  // Process Opcodes with 0 as first byte
  break;
case 1:
  // Process Opcodes with 1 as first byte (only JUMP)
  address = instr & 0x0FFF:
  // Do Jump
  break;
case 2:
  // Process Opcodes with 2 as first byte
.
.
.
}
```

---

### Post by loganwm on 2008-08-05
> **Npl said:**
> Mask out the variable part.
```
unsigned int instr; // your instruction in native endianess
unsigned int address ;

// extract first byte
switch( (instr >> 12) & 0xF)
{
case 0:
  // Process Opcodes with 0 as first byte
  break;
case 1:
  // Process Opcodes with 1 as first byte (only JUMP)
  address = instr & 0x0FFF:
  // Do Jump
  break;
case 2:
  // Process Opcodes with 2 as first byte
.
.
.
}
```

I'm not quite an expert on masking yet :), I understand that the 0xF masks out all but the first byte, but I don't see where the shift twelve comes in?

If someone could explain, I'd be grateful.

---

### Post by dwhitney67 on 2008-08-05
> **loganwm said:**
> ...
Each opcode is a 2-byte value, and my problem is the following example:

The JUMP command is 1NNN where NNN is an address.

I intend to use a switch case, but I don't know how to process an opcode with variable parts like the above?

Can you elaborate a little further on what the "problem" is?  And why is it that you need a switch-case?

Typically a byte is 8-bits long; unsigned bytes can hold values 0x00 to 0xFF.  Thus if you need to mask a byte, the 0xFF is required, not 0xF.  The latter will yield you a nibble.

Where is the NNN coming from?  Are you reading this from a register or just computing it?  If you have a register with 0x1000 and you need to insert NNN, either add it to the register or OR it into the register.

P.S.  If you need to break down the 1NNN, to get the two opcodes:
[PHP]int MSB = (1NNN >> 8) & 0xFF;
int LSB = (1NNN ) & 0xFF;[/PHP]

---

### Post by loganwm on 2008-08-05
Well this is the base that I have worked out for the CPU emulation (I'm currently lacking any real functions, but they'll get worked in.)

```
int process_opcode(int offset) {
	switch (ROM[offset]>>4) {
	case 0:
		printf("Not Implimented\n");
		break;
	case 1:
		//1NNN
		printf("JUMP\n");
		break;
	case 2:
		//2NNN
		printf("Call Sub-Routine\n");
		break;
	case 3:
		//3XKK
		printf("Skip Next Instruction If VX == KK\n");
		break;
	case 4:
		//4XKK
		printf("Skip Next Instruction If VX != KK\n");
		break;
	case 5:
		//5XY0
		printf("Skip Next Instruction If VX == VY\n");
		break;
	case 6:
		//6XKK
		printf("Set VX = KK\n");
		break;
	case 7:
		//7XKK
		printf("Set VX = VX + KK\n");
		break;
	case 8:
		/*
		8XY0 VX = VY
		8XY1 VX = VX OR VY
		8XY2 VX = VX AND VY
		8XY3 VX = VX XOR VY
		8XY4 VX = VX + VY, VF = carry
		8XY5 VX = VX - VY, VF = carry
		8XY6 VX = VX SHR 1 (VX=VF/2), VF = carry
		8XY7 VX = VY - VX, VF = not borrow 
		8XYE VX = VX SHL 1 (VX = VX*2), VF = carry
		*/
		printf("VX Math\n");
		break;
	case 9:
		//9XY0
		printf("Skip Next Instruction If VX != VY\n");
		break;
	case 0xA:
		//ANNN
		printf("Set I = NNN\n");
		break;
	case 0xB:
		//BNNN
		printf("Jump to NNN + V0\n");
		break;
	case 0xC:
		//CXKK
		printf("VX = Random Number AND KK\n");
		break;
	case 0xD:
		//DXYN If N = 0 draws 16x16 sprite, else 8 x N
		printf("Draw Sprite at VX,VY starting at M(I), VF = collision\n");
		break;
	case 0xE:
		//EX9E Skip next instruction if key VX pressed
		//EXA1 Skip next instruction if Key VX not pressed
		printf("Skip Next Instruction If Key Status\n");
		break;
	case 0xF:
		//FX07 VX = Delay timer
		//FX0A Waits a keypress and stores it in VX
		//FX15 Delay timer = VX
		//FX18 Sound timer = VX
		//FX1E I = I + VX
		//FX29 I points to the 4x5 font sprite of hex char in VX
		//FX33 Store BCD representation of VX in M(I)...M(I + 2)
		//FX55 Save V0...VX (X < 8) in memory starting at M(I)
		//FX65 Load V0...VX (X < 8) in memory starting at M(I)
		printf("Not Used");
		break;
	}
}
```

---

### Post by dwhitney67 on 2008-08-05
After looking at your switch statement and the cases, it would seem that you want this:
[PHP]
switch( (ROM[offset] >> 12) & 0xF )
{
  ...
}[/PHP]
If you have two bytes (16 bits), you want to shift it to the left by 12 bits, then AND it with 0xF to yield a value from 1 to 0xF, as per what is needed by the case statements.

To summarize, it appears that you need to derive the most significant nibble of a two byte word.

---

### Post by Npl on 2008-08-06
> **loganwm said:**
> I'm not quite an expert on masking yet :), I understand that the 0xF masks out all but the first byte, but I don't see where the shift twelve comes in?

If someone could explain, I'd be grateful.
You need to get your instruction from somewhere, you apparently use ROM[offset] and I guess its a byte-array/pointer?

If so, then you need to read 2 bytes for the full instruction. If Chip8 is Big Endian:
```
int instr = (ROM[offset] << 8) | (ROM[offset+1]);
```
If Chip8 is Little Endian:
```
int instr = (ROM[offset+1] << 8) | (ROM[offset]);
```

If instr is your full 2-byte instruction, lets take instr = 0x1234 for example (16 bit), then you need to extract the first 4bit. shifting right by 12 bit will result in 0x1, masking out with & 0xF just ensures you dont have further bits to left, its unecessary on many occasions, but a good practice to do it anyway as the compiler should know when he can skip it.

[Bit-Masking on Wikipedia]("http://en.wikipedia.org/wiki/Mask_(computing)")

---

### Post by dwhitney67 on 2008-08-06
I think the OP went out to lunch.

OP -- What is it that you really want????  Don't just answer immediately... think about it for a while, come up with a sincere question... then ask.  If all it deals with is shifting or masking a value, I think with the responses given you should be able help you with such.  If it is something more complicated, let us know.

Sincerely,

Dwhitney67

P.S.  Your work reminds me of what I have done in the past.  Seriously, I have not done anything similar in over 16 years, when I wrote code for an MCU-6801.

---

### Post by loganwm on 2008-08-06
Ah I've had my box running nothing but High Quality video conversions and Bit Torrent downloads for the majority of the last few days so I haven't had much of a chance to get back on and check, I acknowledge that I did kind of make my question vague, but the things I've learned have given me quite a bit of insight into the workings of bit operations.

I currently can't get into my Kubuntu install to mess with my code (Cloverfield and 21 are currently in the middle of a lengthy transcode on my Windows side, so 90% of my processing power is into that)

But incase anyone else cares to toss in anything I might find interesting I'll list the specs of what I'm doing:

Code: C
What: Chip 8 Emulation
Why: Learning experience
How is the ROM loaded: char* array using fread (to ROM)
How is the opcode read: I tried using a short, but it was making me a bit "dizzy" so I might stick to char for the sake of some other reasons
Why use switch(): It's how I read about to emulate a CPU, and it sounds like an efficient way

I don't know how far into this project I'm actually willing to go in the short term, but I definately want to emulate the register handling and conditionals (basically the background stuff) and handle the graphics at a later time.

I don't know if any of you have written an emulator before, but does anyone know the best way to handle graphics emulation?

As always, I'm very greatful for the replies!

---

### Post by dwhitney67 on 2008-08-06
> **loganwm said:**
> ...
I currently can't get into my Kubuntu install to mess with my code (Cloverfield and 21 are currently in the middle of a lengthy transcode on my Windows side, so 90% of my processing power is into that)

Well, at least you have your priorities straight!

Typically speaking, a "short" is a two-byte (16 bit) value.  Using the "<<" or ">>" operations you can shift the bits to the left or to the right, respectively, of that value.

On some systems (actually most), when shifting a 1 from the left-most position (to the right) will in fact carry that 1 indefinitely.  Thus for the following operation (where the % implies binary):
```
value = %1000010111111010;
newValue = value >> 4;   // shift 4 bits to the right...
```
'newValue' will hold the value of '1111100001011111'.

To ensure that newValue retains an unsigned value, you can mask the bits that are of no consequence (i.e. interest):
```
newValue = newValue & 0x0FFF;
```

Naturally, it is easier to merge all of the above into one statement:
```
newValue = (value >> 4) & 0x0FFF;
```
In the case where you want to ignore the first 12-bits, but care about the most significant "portion" of the higher byte (that is bits 12-15):
```
newValue = (value >> 12) & 0x000F;
```
In case you want the first 12 bits (that is bits 0-11), but could care less about the rest:
```
newValue = value & 0x0FFF;
```
Anyhow, I'm sure you know this stuff.  Nevertheless I thought it would be practical to cover the basics.

---

