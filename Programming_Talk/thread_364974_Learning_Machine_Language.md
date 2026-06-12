---
title: "Learning Machine Language"
date: 2007-02-18
forum: Programming Talk
---

### Post by RanKukoo on 2007-02-18
Hello,
   I am a under graduate(IT) in SLIIT (Sri Lanka).  In our course we learned Assembly Language(as a part of subject -Computer Fundamental). Before learning that I thought assembly language is core of other languages. That means, assembly language is the language  that deals with hardware directly.But at the middle of subject I realize it is not true.  I think learning assembly language is good for learning other languages.
   But I want to deal with hardware, execute hardware instructions.I want to make software like Linux KERNEL(if I am right).
   Is there any way to learn these stuff.  Any guide,advice for my success.
       

      Thanks.

---

### Post by g3k0 on 2007-02-18
Noone writes machine language (except crazy people).  Interfacing with hardware is generally done with assembly language and C.  Actually I believe the linux kernal is in C though I am not positive.  Even in the deeper realms of hardware like programming PICs you are using a risc assembly language.  I'm sure you could pick up either languages fairly easy with a book.  You are already learning assembly and C is all over the place.

---

### Post by RanKukoo on 2007-02-19
// I think this is may be a mad question.
I don't know about the bootstrapping process too depth.
If there is no platform, how do I run a software written in C or assembly language.If I want to create a platform, How do I create?

---

### Post by gradedcheese on 2007-02-19
You take the processor you're using (lets say ARM) and grab its documentation.  The documentation will give you a list of instructions that the processor supports (ex: move, load, store, branch).  Those instructions map, one-to-one to assembly language.  You can then program in ARM assembly.  You write some ARM assembly code that initializes the processor from boot: sets up some interrupts, initializes the stack and sets the stack pointer, and so on.  Now it can run a C program.  Why?  Well, you've compiled the C program with an ARM-target compiler and toolchain, and in the end it produced ARM assembly and an ARM binary (ie: a sequence of ARM instructions).  You put that binary into memory somewhere and your initialization routine jumps to that address once it's ready.  Suddenly your processor is running C code.  The Linux Kernel, by the way, is written entirely in C.

If you're interested in very low-level design, you're looking at CPU design.  There's plenty of stuff going on there, and it's pretty interesting.  The term is usually "Computer Architecture" or "Processor Architecture".  

If you're interested in this stuff, take a look at a small microcontroller like the Atmel AVR or the Freescale HC12.  There you'll be handed a nice instruction/assembly manual and you can code right away on a real system.  You can then write your own little operating system or anything else that interests you.

Have fun.

---

### Post by Lux Perpetua on 2007-02-19
> **RanKukoo said:**
> // I think this is may be a mad question.
I don't know about the bootstrapping process too depth.
If there is no platform, how do I run a software written in C or assembly language.If I want to create a platform, How do I create?That's the thing about compiled languages like C (and trivially assembly): they don't require a "platform" at all; they run on the hardware.

---

### Post by Wybiral on 2007-02-19
> **RanKukoo said:**
> ... Before learning that I thought assembly language is core of other languages. That means, assembly language is the language  that deals with hardware directly.But at the middle of subject I realize it is not true...

What isn't true about that? There is a slight difference between machine code and assembly language... Assembly language gets assembled into machine code... BUT, assembly language is really just a human readable version of machine code (in reality, there is a byte for almost every opcode)

Anyway... Other languages do eventually break down into machine code (even interpreted and VM'd languages)... It's the only byte format that will communicate with the processor. When a C/C++ program (as an example) gets compiled, it goes from C/C++ to assembly, then from that assembly to machine code... It's executable form.

My advice... If you already know some assembly, learn C. Even if you do need to cover parts of it in assembly, you can dump your C program to assembly before it gets assembled (remember, it goes through an assembly stage when it's being compiled). With gcc, the flag to dump the assembly is "gcc myCProgram.c -S" then it will produce "myCProgram.s" which contains the equivalent assembly code... You can then insert/optimize things at that level, and use gcc to assemble it with "gcc myCProgram.s"

In linux, the best assemblers I've ran across are NASM and GAS. GAS, btw, is the GNU assembler (it's what gcc uses after it compiles to assembly)

> Noone writes machine language (except crazy people).
I occasionally use assembly and machine code (and I don't think I'm crazy). It allows you to fine tune your compiled code and optimize things as much as possible... While giving you a more enlightened idea of what goes on when you run a program... Since machine code is what actually communicates with the processor.

EDIT:

OH... it sounds like you want to write your own OS and are wondering how to do the boot part...
[http://www.joelgompert.com/OS/lesson1.htm](http://www.joelgompert.com/OS/lesson1.htm)
[http://my.execpc.com/~geezer/osd/boot/index.htm](http://my.execpc.com/~geezer/osd/boot/index.htm)
[http://linuxgazette.net/issue77/krishnakumar.html](http://linuxgazette.net/issue77/krishnakumar.html)
[http://www.osdev.org/osfaq2/](http://www.osdev.org/osfaq2/)
[http://www.groovyweb.uklinux.net/index.php?page_name=how%20to%20write%20your%20own%20os](http://www.groovyweb.uklinux.net/index.php?page_name=how%20to%20write%20your%20own%20os)

---

### Post by graeme_p on 2007-02-19
There are websites with information and howtos on [linux kernel hacking]("http://www.kernelhacking.org/") and writing drivers. You may also be able to find some books on processor architecture (does SLIIT have a reasonable library?). Once you are reasonably good at C you will probably find opportunities to help.

In general the hardware manufacturers will make sure that there is a C compiler for their platform, so you are not likely to need to go from bare metal. I did know someone who did write machine code directly because it was a new platform with no assemblers or compilers, but he did that 25 or thirty years ago.

---

### Post by rplantz on 2007-02-19
There is a very important reason why you should not write in machine code -- nobody else can understand what you have written. And neither can you about a week after you have written it. A big advantage of assembly language is that it is much easier to read. Even assembly language is difficult to read if the author has not used good comments. Again, this includes the author a week or so after he/she has last worked on it.

I have been writing in assembly language for over forty years, on a dozen or so machines. I can recall using machine language only twice. Once was in 1974. I had to boot a minicomputer by loading the instructions in from switches on the front panel. A couple of years later I was designing a device driver for a CT scanner. I had code in there that modified an instruction while the program was running in order to speed things up. Yes, it was self-modifying code. 

About twenty years ago I learned C. I love assembly language, but I would never use it on a real-world project unless I had to. To give you an idea of how C can be used to access low-level I/O devices, here is a snippet of some code I wrote to send a single character to a DUART:
```

typedef unsigned char ubyte;
#define SR 0x03
#define TB 0x07
#define TxRDY 4
#define PORTA 0x00
#define PORTB 0x10
#define DUART (ubyte*) 0xFF0000
#define LINEFEED 0x0A
#define RETURN 0x0D

void charout( int c )
{
   register ubyte* port = (ubyte*) DUART+PORTA;
   
   while ((*(port+SR) & TxRDY) == 0)
      ;
   *(port+TB) = c;
   
   if (c == LINEFEED)
      charout (RETURN);
}

```
The system uses memory mapped I/O. The DUART is at address 0xFF0000. It has two ports; port A at 0x00 and port B at 0x10 relative to the base location of the DUART. The algorithm waits until the transmission ready bit in the status register goes to zero. Then it send the character to the transmission buffer. If the character was the linefeed, it also sends a return character.

I wrote this several years ago and have not looked at it for nearly three years. The algorithm was immediately clear to me when I read this C code. It's for a Motorola 68000, which I know quite well. I can guarantee that it would have taken me at least 1/2 hour to recall the algorithm if I had simply read the machine code for this function.

If you wish to do low-level hardware programming, my recommendation is that you learn C really well, including how to embed assembly language into your C functions. You need to understand CPU architectures, which will require you to learn about machine code. But I think it would be very unusual if you ever find yourself actually writing in machine code.

---

### Post by g3k0 on 2007-02-21
> **Wybiral said:**
> 
I occasionally use assembly and machine code (and I don't think I'm crazy). It allows you to fine tune your compiled code and optimize things as much as possible... While giving you a more enlightened idea of what goes on when you run a program... Since machine code is what actually communicates with the processor.

I was speaking of pure machine code.  1's and 0's, not assembly.  If you do write out 1's and 0's I will try to find you a good doctor.

---

### Post by willz06jw on 2007-07-12
I had an earlier post about this also --- tell me, no matter how idiotic it is, can anyone tell me how to write the 0s and 1s into NASM or GAS?  I just want to do it to say I have done it --- Are you man [Edit: Nerd] enough to tell me how?

Will

---

### Post by Wybiral on 2007-07-12
> **g3k0 said:**
> I was speaking of pure machine code.  1's and 0's, not assembly.  If you do write out 1's and 0's I will try to find you a good doctor.

No one write machine code in 1's and 0's... But we do use hex sometimes which us just another form of those 1's and 0's (where each byte relates to 8 bits)

It's not that hard... As I was saying, assembly DIRECTLY correlates to machine code (there is basically a byte for each mnemonic).

Sometimes I use it in other programs (sometimes you need a function to generate some machine code, or you need to know how many bytes a chunk of code is, so you have to know how it is assembled).

I don't think I need a doctor, someone has to do it, or none of your HLL's could exist.

---

### Post by AlexThomson_NZ on 2007-07-12
[http://www.cengizhan.com/content/binary/RealProgrammers.jpg](http://www.cengizhan.com/content/binary/RealProgrammers.jpg)

---

### Post by Modred on 2007-07-13
> **Wybiral said:**
>  As I was saying, assembly DIRECTLY correlates to machine code (there is basically a byte for each mnemonic).

Not entirely true, depending on your processor.  If you're using a RISC (reduced instruction set computer) such as Sun Ultras, IBM PowerPCs, and similar, then each assembly instruction directly correlates to a machine code.  However, on CISC (complex instruction set computer) systems, such as Intels and AMDs, there is actually a microcode layer between assembly and machine code.

With CISC, some assembly instructions transfer directly to machine code. Examples:

```

mov ax,1A
mov bx,2

```

Other commands actually execute multiple microcode instructions. Example:

```
mul bx
```

Last I checked, the debate over if RISC actually gave better performance than CISC has mostly subsided with the advent of multi-core CISC processors.  I may be mistaken.

---

### Post by Wybiral on 2007-07-13
> **Modred said:**
> Not entirely true, depending on your processor.  If you're using a RISC (reduced instruction set computer) such as Sun Ultras, IBM PowerPCs, and similar, then each assembly instruction directly correlates to a machine code.  However, on CISC (complex instruction set computer) systems, such as Intels and AMDs, there is actually a microcode layer between assembly and machine code.

With CISC, some assembly instructions transfer directly to machine code. Examples:

```

mov ax,1A
mov bx,2

```

Other commands actually execute multiple microcode instructions. Example:

```
mul bx
```

Last I checked, the debate over if RISC actually gave better performance than CISC has mostly subsided with the advent of multi-core CISC processors.  I may be mistaken.

I know there are certain special cases, my point was that even people who do occasionally have to deal with machine code don't sit there and type 1's and 0's, it's generally hex. And the hex values relating to each mnemonic aren't too hard to memorize (if that's your thing).

---

### Post by ankursethi on 2007-07-13
This is interesting.

I was wondering, can you use QEmu or some other virtual machine to run those toy operating systems mentioned in one of the replies? Can you build an OS under QEmu without frying your own PC?

---

### Post by pmasiar on 2007-07-13
I could argue that if operation has binary code, it is machine code instruction, regardless how it is implemented in microcode (directly or by multiple microcode commands). 
> **Modred said:**
> 

Other commands actually execute multiple microcode instructions. Example:

```
mul bx
```


Microcode is implementation details from POV of programmer - unless you are allowed to dive in and program in microcode. And it would make sense only in CPU allows loading external microcode. Last time I checked (in PDP/11 - it allowed custom microcode) it was hairy enough so I was not interested since :-)

There are few brave souls willing to dive in (can you imagine how hard is to debug anything?), but most of the "bread and butter" programming is on application side, and knowledge of machine language just helps you to be more efficient app developer (don't expect miracles and magic from compiler - it has to be translated to machine language, and it is very stupid).

---

### Post by purple_kv on 2008-06-17
[COLOR="Indigo"]Started a new thread with this post.  Wouldn't find how to totally delete it so I just changed it.
[/COLOR]

---

### Post by Lster on 2008-06-17
[QUOTE=ankursethi]I was wondering, can you use QEmu or some other virtual machine to run those toy operating systems mentioned in one of the replies? Can you build an OS under QEmu without frying your own PC?[/QUOTE]

I have used Qemu to create my own OS. It's slow development, but fun all the same. I used this tutorial at first:

[http://osdever.net/bkerndev/Docs/intro.htm](http://osdever.net/bkerndev/Docs/intro.htm)

It doesn't cover much, but it does provide code at the end with very basic functionality. On top of that one would need to add memory management, a substantial API, multitasking, driver support, graphics and sound support (other than textual graphics), functions to read data from a hard disk (and functions to manage files), etc...

---

### Post by Lux Perpetua on 2008-06-17
For future reference: since you are not replying to the original topic, you should post a new thread.

**edit:** This is in reply to purple_kv.

---

### Post by purple_kv on 2008-06-17
[COLOR="Indigo"]Sorry about not starting a new thread.  I am not familiar with this forum.   

This puzzle it driving me nuts! Still no solution even with additional advice.  [/COLOR]

---

### Post by PaiPimenta on 2008-08-18
I'm a crazy person, just starting out, and I've found the following resource quite helpful:

- Machine & Assembly Language Programming, by David C. Alexander (c) 1982

I think, in the long run, what most of the people on this post are saying is right: there is little value you will take away from being able to (and having spent and/or wasted the time writing) code a simple operation or entire program in binary machine code.  However, I think that this message is as convoluted as my PsychoBio prof saying that "you don't have to memorize this."  He in fact meant that we should not only know it by heart, but understand it at the depth to be able to extrapolate, speculate about novel interactions/circumstances.  I think that learning about number systems (dec, bin, hex, oct), logic circuits and gates, hardware implementation, and machine/assembly is all a foundation that certain crazies prefer to delve into.

You're honestly going to have to deal with hex from a resource point of view.  Many examples from the web and that Alexander source I mention use hex in their machine code.  (I personally recommend number conversions [and logic diagrams, for that matter] as a bank line passtime.)

Just by typing ```
apropos machine
```, I see that there is a Tcl command ```
load
``` that can load machine instructions directly.

I myself am trying to go about learning machine and assembly on an iBook G4 (sadly still running OS X) and my desktop AthlonXP 1800 machine running Ubuntu.

There is also a good book, freely available online called "Programming From The Ground Up."  Just Google it for the pdf.  This is assembly, but maybe the author could at least point you in the right direction?

---

### Post by PaiPimenta on 2008-08-18
And if you know assembly, you can assemble your assembly source code with "as" into object files: ```
as -o program.o program.s
```
Then, you can view the object file in hex using an editor like VIM:
```
vim program.o
```
Then once you're in VIM:
```
:%!xxd
```
Changes the editor to view in hex.

This assembly program: 
```
.section .data

.section .text
.globl _start
_start:
 movl $1, %eax    # this is the linux kernel command
                  # number (system call) for exiting
                  # a program

 movl $0, %ebx    # this is the status number we will
                  # return to the operating system.
                  # Change this around and it will
                  # return different things to
                  # echo $?

 int $0x80        # this wakes up the kernel to run
                  # the exit command

```
...creates this machine code ...
```

0000000: 7f45 4c46 0101 0100 0000 0000 0000 0000  .ELF............
0000010: 0100 0300 0100 0000 0000 0000 0000 0000  ................
0000020: 6c00 0000 0000 0000 3400 0000 0000 2800  l.......4.....(.
0000030: 0700 0400 b801 0000 00bb 0000 0000 cd80  ................
0000040: 002e 7379 6d74 6162 002e 7374 7274 6162  ..symtab..strtab
0000050: 002e 7368 7374 7274 6162 002e 7465 7874  ..shstrtab..text
0000060: 002e 6461 7461 002e 6273 7300 0000 0000  ..data..bss.....
0000070: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000080: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000090: 0000 0000 1b00 0000 0100 0000 0600 0000  ................
00000a0: 0000 0000 3400 0000 0c00 0000 0000 0000  ....4...........
00000b0: 0000 0000 0400 0000 0000 0000 2100 0000  ............!...
00000c0: 0100 0000 0300 0000 0000 0000 4000 0000  ............@...
00000d0: 0000 0000 0000 0000 0000 0000 0400 0000  ................
00000e0: 0000 0000 2700 0000 0800 0000 0300 0000  ....'...........
00000f0: 0000 0000 4000 0000 0000 0000 0000 0000  ....@...........
0000100: 0000 0000 0400 0000 0000 0000 1100 0000  ................
0000110: 0300 0000 0000 0000 0000 0000 4000 0000  ............@...
0000120: 2c00 0000 0000 0000 0000 0000 0100 0000  ,...............
0000130: 0000 0000 0100 0000 0200 0000 0000 0000  ................
0000140: 0000 0000 8401 0000 5000 0000 0600 0000  ........P.......
0000150: 0400 0000 0400 0000 1000 0000 0900 0000  ................
0000160: 0300 0000 0000 0000 0000 0000 d401 0000  ................
0000170: 0800 0000 0000 0000 0000 0000 0100 0000  ................
0000180: 0000 0000 0000 0000 0000 0000 0000 0000  ................
0000190: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001a0: 0300 0100 0000 0000 0000 0000 0000 0000  ................
00001b0: 0300 0200 0000 0000 0000 0000 0000 0000  ................
00001c0: 0300 0300 0100 0000 0000 0000 0000 0000  ................
00001d0: 1000 0100 005f 7374 6172 7400 0a         ....._start..

```

There you have it! Now convert these from hex to binary, find a way to edit in binary (not hex) and compile, and you have your shiny Ice Age acorn finally!

---

### Post by pmasiar on 2008-08-18
> **PaiPimenta said:**
> "you don't have to memorize this." 

My professor of calculus used to say: the more you can figure out, the less you have to remember. His entire notes for 5 semesters of calculus were on single page of paper. He was third in family teaching calculus: his granddad was first head of department, and his dad wrote one of the classic texbooks about the subject.

Of course his lectures were incredible (including dry wit), but it was only later i fully recognized it.

And as a programmer, I know that numbers (floats) do not work as he thought they do :-)

OK back to topic: assembly changes, every processor is different. That's why we have C: if you are systems programmer, do as much as you can in C. If you are compiler writer, write utilities which will generate ASM for you according to what your processor has. It is interesting to know (one) CPU architecture, but it is icredibly slow slog to program anything useful in such low level language as any ASM is.

---

