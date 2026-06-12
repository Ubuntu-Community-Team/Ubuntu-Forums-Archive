---
title: "Run Assembly or C directly on the processor (no OS, just you and the hardware)"
date: 2009-06-19
forum: Programming Talk
---

### Post by oodlesOfmoodles on 2009-06-19
This may be a silly questions, but how do I load a program directly onto the processor? If I have a program written in a version of assembly supported by my processor how do I load it and run it directly?

Thanks so much!

---

### Post by slavik on 2009-06-19
connect ROM to it and put the code at the proper address.

---

### Post by oodlesOfmoodles on 2009-06-19
Is there no way to run code off of the RAM and use the BIOS to load your program?

---

### Post by NielsBhor on 2009-06-19
Well, you need some sort of synthesizer such as Xilinx or whatever....an FPGA board with a ROM....and learn VHDL or Verilog

There is no way to run assembly or C directly on a processor. You need to talk in terms of bits, microprogram code, and know what to bits correspond to different addressing modes such as indirect, direct, immediate, extended addressing modes.

The processor only speaks in voltages, not assembly or C.

And, you must know how to route the bits to turn on what features of the CPU you want to use such as the ALU, Shift Registers, FPUs, etc...

---

### Post by Mirge on 2009-06-19
> **NielsBhor said:**
> Well, you need some sort of synthesizer such as Xilinx or whatever....an FPGA board with a ROM....and learn VHDL or Verilog

There is no way to run assembly or C directly on a processor. You need to talk in terms of bits, microprogram code, and know what to bits correspond to different addressing modes such as indirect, direct, immediate, extended addressing modes.

The processor only speaks in voltages, not assembly or C.

And, you must know how to route the bits to turn on what features of the CPU you want to use such as the ALU, Shift Registers, FPUs, etc...

Ignorance is bliss... that just made my head hurt a little bit.

---

### Post by phrostbyte on 2009-06-20
Do you mean running C code without an OS? You can do this actually the Linux kernel itself is mostly written in C. BIOS will just load and execute the first 512 bytes of a partition. But to have a long running program you have to do some initialization especially like the interrupt table and that must be done with assembly. When you do something like divide by zero, the processor throws an exception, so you must write exception handlers to handle these or your processor will halt instead.

---

### Post by croto on 2009-06-20
If you want to run some code without the operating system, the easiest way would be to load your code at boot time. I'm sure you can find info on the web, but in a nutshell, it would be like this.

When the computer starts up (it starts up in real mode, 8086 emulation) bios will try read the boot sector on floppy, hard drive, cdrom (the order can be set on bios setup). Whatever finds first, the boot sector (first sector on disc) gets loaded in memory 0000:7C00, and the jumps to that address. 

So what you want to do is put your code in the boot sector. You'll have to write it in assembly, make sure it fits in 512 bytes (1 sector), make it load the rest of the code from other sectors in the hard drive if it's larger, use bios for I/O, etc.

Nice project actually. Good luck!

---

### Post by NielsBhor on 2009-06-20
Interesting about the BIOS. 

Instead of using the FPGA board to do softprocessor implementation, you could have a program stored in the first 512 bytes of memory that will compile the C code or the assembly code that you have. Well, so little memory to even compile. Linux C code for the MBR is already compiled beforehand to machine code. What you need to do first is have your C code or assembly compiled to machine code at runtime. 

To the OP, you know what's involved now. Complex, and it could be done theretically.

---

### Post by smartbei on 2009-06-20
Come on now...
The OP didn't actually mean running assembly or c code at on the CPU, **uncompiled!** (so compilation at boot is necessary). He meant compiling code, and having it run instead of the operating system. croto's answer is very good - though the question remains, what is it you are trying to accomplish?

BTW -> **Mirge said:**
> Ignorance is bliss... that just made my head hurt a little bit.
That made my day :-)

---

### Post by NielsBhor on 2009-06-20
He didn't provide enough information for that.

---

### Post by fr4nko on 2009-06-20
I don't know if I well understood the initial question but there is a way to execute arbitrary code in C. Here an example:
```
#include <stdio.h>

static const char myfact[] = {
0x55,                   /*    push   %ebp */
0xb8, 0x01, 0x00, 0x00, 0x00,       /*    mov    $0x1,%eax */
0x89, 0xe5,                /*    mov    %esp,%ebp */
0x8b, 0x4d, 0x08,             /*    mov    0x8(%ebp),%ecx */
0x83, 0xf9, 0x01,             /*    cmp    $0x1,%ecx */
0x7e, 0x1b,                /*    jl0xe,    0x2b, <myfact+0x2b> */
0x8d, 0x51, 0xff,             /*    l0xea,    -0x1(%ecx),%edx */
0x89, 0xc8,                /*    mov    %ecx,%eax */
0x83, 0xfa, 0x01,             /*    cmp    $0x1,%edx */
0x74, 0x11,                /*    j0xe,     0x2b, <myfact+0x2b> */
0x8d, 0xb6, 0x00, 0x00, 0x00, 0x00,    /*    l0xea,    0x0(%esi),%esi */
0x0f, 0xaf, 0xc2,             /*    imul   %edx,%eax */
0x83, 0xea, 0x01,             /*    su0xb,    $0x1,%edx */
0x83, 0xfa, 0x01,             /*    cmp    $0x1,%edx */
0x75, 0xf5,                /*    jn0xe,    0x20, <myfact+0x20> */
0x5d,                   /*    pop    %ebp */
0xc3,                   /*    ret     */
};

int
main ()
{
  int n, r;
  int (*fact)(int) = (int (*)(int)) myfact;

  while (1) {
    puts ("Choose an integer: ");
    scanf ("%d", &n);
    r = fact (n);
    printf ("The factorial of %d is %d\n", n, r);
  }

  return 0;
}

```The hexadecimal code is the equivalent of the following function:
```
int
myfact (int n)
{
    int j, p;
    if (n <= 1)
        return 1;
    p = n;
    for (j = n - 1; j > 1; j--)
        p *= j;
    return p;
}

```Francesco

---

### Post by CptPicard on 2009-06-20
I do not understand the question. Native-compiled code already runs "directly on the processor", it's not as if the OS is some kind of interpretation layer in between or anything, although it gives certain services...

---

### Post by NielsBhor on 2009-06-20
It's weird. Lots of stuff is missing from his questions. It is unanswerable. And, given the fact at the hardware level, you're thinking in terms of binaries not higher level languages. Not only that the compiler must be made using just binaries.

The code for this binary compiler must be small enough like the brainfu*ked program.

[http://home.arcor.de/partusch/html_en/bfd.html](http://home.arcor.de/partusch/html_en/bfd.html)

Leave the hardware level for the computer engineers. Don't waste your time. If you're doing embedded systems, use the development kit available for that platform. Or, if you want to hard code a processor, use an FPGA like the Virtex 2 from Xilinx or the Spartan 3e. You must code your own VGA drivers, Keyboard drivers, or you may use the integrated softprocessor such as the picoblaze or microblaze.

---

### Post by croto on 2009-06-20
I do not agree about the need to write the compiler again. First, I think the best language for OP's goal would be assembly. Either way, assembly or C, the code needs to be assembled/compiled before it is even deployed to disk/memory for execution. That would be done using the regular compiler and os tools. One only needs to make sure the code generated does not use any OS calls (only bios), and that it can run in the conditions it will run when it loaded by bios.
Depending on what the OP want to do, the project ranges from doable to impossible. If he wants to display "Hello world" on the screen, that's pretty doable, and that's where I would start from. If he wants to have a full blown app running without any OS, the fact that he is asking how to do it makes me think that it would take him years of study to get there.

---

### Post by hessiess on 2009-06-20
Programming for bare hardware isn't something I know much about, but Look into programming for game consoles like the GBA, where everything is written directly on the hardware with no OS.

---

### Post by mmix on 2009-06-21
[see coreboot's romcc](http://stackoverflow.com/questions/713734/execution-without-os/718950#718950)

---

### Post by soltanis on 2009-06-21
Doh? Sounds like OP wants to know how to write an operating system. First of all, you need advanced knowledge of assembly programming, how your computer works, and the boot time workings of a system; someone above talked about the boot sector and how the BIOS starts in real-mode then jumps to a specific address. That's the start.

Then you'll need to interface with the devices on the system to perform any sort of I/O tasks.

Oh, and if you want to run C code, you're going to have to write your own C library. No libc for you.

So um, yeah. You'll be in for it, unless you're writing code for an embedded platform.

Why do you want to do this again?

---

### Post by bryanc on 2009-07-22
He means programming in assembler without an OS executing his code.  I'm trying to do the same thing.  There's a tutorial available about booting using only assembler/c in the master boot record of any device.  

You write the 16-bit assembler code to set up a stack in real-mode and call an external function (about 10 lines of code)
Then you can start programming in 32-bit protected mode in c, using assembler to interact directly with BIOS.
A simple DOS batch file links the c code and the assembler code into executable native binary.  
Then you use a tool to write the resulting com file to the MBR of a flash drive.
Reboot with the flash drive in your USB port, and if all works, your processor will execute your code. 

Interrupts are different than interacting with DOS, because you no longer have that DOS layer in between you and the processor.  

You are in effect writing your own OS, but it can just be a simple "hello world" program to start. 

[http://www.codeproject.com/KB/tips/boot-loader.aspx](http://www.codeproject.com/KB/tips/boot-loader.aspx)

---

