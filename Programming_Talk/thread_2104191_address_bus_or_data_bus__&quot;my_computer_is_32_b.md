---
title: "address bus or data bus? / &quot;my computer is 32 bit&quot;"
date: 2013-01-12
forum: Programming Talk
---

### Post by IAMTubby on 2013-01-12
Hello,
I have been trying to understand the difference between data bus and address bus. I now understand that data bus can be thought of as the size of the memory block you are writing to, whereas address bus tells you the total number of such addresses that are open to such writing/reading.

But I wrote this small program and this has left me totally confused.
```

#include <stdio.h>

int main(void)
{
 char* str;
 int a = 5;
 str = malloc(200 * sizeof(char));

 printf("\nsizeof(void*) == [%d]",sizeof(void*));
 printf("\nsizeof(a) == [%d]",sizeof(a));
 printf("\naddress of str == [%x]",str);

 return 0;
}

```

The output is : 
```

sizeof(void*) == [4]
sizeof(a) == [4]
address of str == [85a9008]
```

Based on the above, these are my questions
1.sizeof(void*) == [4]. Is this the size of my data bus or address bus ? **I think it's the size of my address bus, because void* is a pointer.**

2.sizeof(a) == [4]. **I think this is the size of my data bus**

3.address of str == [85a9008]. I can't decipher this at all. I'm printing in hex(check code). **And a 7 digit hex number, means 28 bits ? What ?? my "some bus" is 28 bits ?**

4.When people say, "my system is cooler than yours cuz mine is 64 bit", does that mean 64 bit is the address bus or data bus size ? **-  I think data bus, because that would mean 64 bit instructions can be performed at once.**

5. How is the size of a register related to data bus/address bus ? I have heard of ax,bx,cx,dx resgisters ? But are these part of data bus or address bus ?

Thanks.

PS : I know that 64 bit can be for both the hardware as well as the OS. A 32bit x-86 ubuntu 12.10 on a 64-bit dell latitude or a  
64bit amd-64 ubuntu 12.10 on a 64 bit machine. 
But always the hardware has to be higher compared to the OS.(as in 64 vs 32)

---

### Post by linuxonbute on 2013-01-12
You seem to be totally confused.
You can easily find these things out by doing a search with google.
try this for an explanation:
[http://en.wikipedia.org/wiki/System_bus](http://en.wikipedia.org/wiki/System_bus)

---

### Post by MadCow108 on 2013-01-13
buses are a part of the hardware design, you pretty much never have to know anything about them in software programing (except maybe some firmware stuff and really low level hardware drivers)

what is the context of these questions? do you want to learn about hardware design or software design?

the physical implementation of buses is not visible in cpu programming (assembler/C)

> 1.sizeof(void*) == [4]. Is this the size of my data bus or address bus ? I think it's the size of my address bus, because void* is a pointer.
it has (directly) nothing to do with the bus itself, its simply the size of the pointer, which depends not on the hardware but on the ABI you are prgramming for (32 bit in 32 bit mode (i386), or 64 bit in long mode (amd64)
amd64 cpu's can handle both modes.
e.g. itanium only has a long mode (which is different from amd64)

>  2.sizeof(a) == [4]. I think this is the size of my data bus
similar this is the size of an int, which is again only dependent on the ABI not actual hardware.

>  3.address of str == [85a9008]. I can't decipher this at all. I'm printing in hex(check code). And a 7 digit hex number, means 28 bits ? What ?? my "some bus" is 28 bits ?
%x will not zero pad to 4-8byte, use %p to print pointers in their proper representation including zero padding.

>  4.When people say, "my system is cooler than yours cuz mine is 64 bit", does that mean 64 bit is the address bus or data bus size ? - I think data bus, because that would mean 64 bit instructions can be performed at once.
it means its an amd64 cpu, which can run 32 bit and 64 bit code, the internal cpu wordsize is 64 bit and it has a more modern instruction set, most notable good support for position independent code and vectorized instructions (SSE2)
It also has 16 registers compared to i[3456]86 which only has 8

>  5. How is the size of a register related to data bus/address bus ? I have heard of ax,bx,cx,dx resgisters ? But are these part of data bus or address bus ?
the size of the register is the internal wordsize of the cpu so 64 bit on amd64, registers and buses are different things.

---

### Post by trent.josephsen on 2013-01-13
Just to add to what MadCow said, it's possible to build a CPU that operates on values larger (or smaller) than its address or data bus; for instance, the original Motorola 68k has an external 24-bit address bus, but uses 32-bit addresses internally; it has 32-bit data registers and a hybrid 16/32 bit instruction set, but comes in editions with 16-bit and 8-bit data buses. All this would be essential information if you were designing a computer around the 68k, but if you were programming it in C such information would normally be completely transparent. You wouldn't be able to tell, without resorting to compiler tricks, whether you were running on a version with an 8-bit or a 16-bit data bus.

Buses are, basically, strips of copper. They're only loosely correlated with the sizes of types provided by your ABI.

---

### Post by xb12x on 2013-01-13
> **MadCow108 said:**
> the physical implementation of buses is not visible in cpu programming (assembler/C)

MadCow108, your answer is well written and informative.

But just to add to this thread: there are certain "calls" you can make to certain CPU's that can directly or indirectly tell you what the size of the buses are.

Intel, for example, provides Machine Specific Registers (see MSR) and other specialized internal CPU registers.

---

### Post by trent.josephsen on 2013-01-13
> **xb12x said:**
> But just to add to this thread: there are certain "calls" you can make to certain CPU's that can directly or indirectly tell you what the size of the buses are.

Really? At runtime? I'm not very familiar with x86; can you provide an example of how this might be done?

---

### Post by xb12x on 2013-01-13
> **trent.josephsen said:**
> Really? At runtime? I'm not very familiar with x86; can you provide an example of how this might be done?

Well, the easiest answer is that on a Linux system it's done for you. Read the Linux Programmer's Manual pages for msr and cpuid (by entering **man msr** and **man cpuid** on your Linux system). Or Google **linux man msr** and **linux man cpuid**.

If you want to do it by directly accessing the CPU then get the **Intel 64 and IA-32 Architectures Software Developer's Manuals**. They are free to download from the **Technical Document Libraray** on Intel's web site ([www.intel.com](www.intel.com)).

---

### Post by ofnuts on 2013-01-14
> **trent.josephsen said:**
> 
Buses are, basically, strips of copper. They're only loosely correlated with the sizes of types provided by your ABI.

Not speaking of a very loose definition of "bus". Is this the external chip pins used to access memory on the motherboard, or the connection between processor and the L1 data cache?

Btw, I don't think we will ever see a processor with a 64-bit address bus in any near future...

---

### Post by trent.josephsen on 2013-01-14
Ok, maybe I should have said "long conductors" instead of "strips of copper". I was still thinking in terms of the 68000, which doesn't have internal cache and so that point is moot. But for a more complicated chip you could definitely apply the word "bus" to the internal connections between different functional units.

On the other hand, you could make an argument that "the" data bus consists of those and all similar buses put together (along with some decoding and caching logic), and the "width" of the bus is that of the narrowest part.

---

### Post by IAMTubby on 2013-01-15
**> **linuxonbute said:**
> **
> **MadCow108 said:**
> 
> **trent.josephsen said:**
> 
> **ofnuts said:**
> 
> **xb12x said:**
> 
Thanks a lot for your wonderful replies, I have read them and have a better idea now, but I need a few more hours to think about it and before I can respond individually.
Thanks a lot once again :)

---

