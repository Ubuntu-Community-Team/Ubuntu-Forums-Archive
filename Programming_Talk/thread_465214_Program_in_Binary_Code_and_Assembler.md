---
title: "Program in Binary Code and Assembler?"
date: 2007-06-05
forum: Programming Talk
---

### Post by willz06jw on 2007-06-05
Howdy and thanks for readin,

I am trying to find the easiest way (AKA which programs do I use)  to create a program in Binary Code that will run in Ubuntu.

Now I know this is a strange and eclectic question, but I have programmed a bit in my time and I am ready to try to further my understanding by trying this for fun.  

I am also interested in learning assembler (for device driver programming), so any help on what I could use for that would also be greatly appreciated.

Thanks Ubuntu guys/gals,
Will from Texas

btw:  Is Binary Code faster than Assembly Language?

---

### Post by meatpan on 2007-06-05
> **willz06jw said:**
> 
btw:  Is Binary Code faster than Assembly Language?

Programming languages are converted to binary code by a compiler at compile time or an interpreter at run time, so a machine does not truly run assembly code.

If you want to learn assembly, a great command that can help is 'objdump'.  You can use this powerful utility to output the assembly code from a standard linux ELF executable.  For example, ff you have an elf exe named a.out, run 'objdump -S a.out' to see the assembly code.  The first column is the instruction location, the second is the actual instruction (this is in hex notation), and the third/fourth columns are the associated assembly instructions.    Also consider using a compiler, such as gcc, to produce assembly output.  In gcc this can be done by compiling with the '-S' flag.   In this way you can analyze your original source code, and the resulting assembler representation according to gcc.


In college I used a book, 'Computer Systems, A Programmers Perspective', by Bryant/Ohallaran, that had an excellent chapter on assembly code.   The book walks you through some basics, and helps you understand how to identify and write typical programming idioms in assembly code.  The examples were using gcc produced assembler, so it should work great with ubuntu.

---

### Post by willz06jw on 2007-06-05
So there is no modern equivalent to the binary punch cards used in the 50s?

Will

---

### Post by Ramses de Norre on 2007-06-05
Why on earth would someone want to write directly in binary... Talking about bug-prone and unreadable code...
The only goal I can see is learning the very fundamentals of processors but I doubt you should learn these things with an OS between you and the processor.

---

### Post by aks44 on 2007-06-05
There is one equivalent : an hex editor.

I once wrote a Windows (PE) executable like that. The thing only displayed a MessageBox, but it took me several hours to put it together (not mentioning all the reading I did beforehand).

IOW, why on earth would you ever want to do a thing like that?
Assembly mnemonics have a one-to-one relationship with the corresponding binary code, so if you really want to get that close to the metal, at least assembly is human readable.

One thing you should know however : premature optimization is the root of all evil.

Better write your program using a higher level language, profile it, and IF any bottleneck arise in a CPU-bound area of your code, then and only then should you consider switching to assembly. But even before that should you try to optimize the concerned algorithm, as assembly is very painful to write and maintain...

---

### Post by Henry Rayker on 2007-06-05
If you want to code as low level as possible, do assembly. Coding in binary is stupid and pointless. The assembly code will translate exactly to one binary sequence (assuming no compiler optimizations, for example, converting a divide by two to a left bit shift). One of my courses my first year of college required that we do some code in binary and it was a total pain in the ***. There is nothing much to learn aside from the fact that a binary sequence is generated from assembly code.

---

### Post by KaeseEs on 2007-06-05
> **Henry Rayker said:**
> If you want to code as low level as possible, do assembly. Coding in binary is stupid and pointless. The assembly code will translate exactly to one binary sequence (assuming no compiler optimizations, for example, converting a divide by two to a left bit shift). One of my courses my first year of college required that we do some code in binary and it was a total pain in the ***. There is nothing much to learn aside from the fact that a binary sequence is generated from assembly code.

This man is right.  Assembly language instructions for a given architecture represent exactly binary instructions for the processor.  For example, the x86 uses 32-bit instructions.  The processor expects a stream of alternating instructions and data segments. For example:```
        xor     ebx,ebx;   set second reg to zero
```would be translated during compilation to something like```
        31      db
```...which is a hexadecimal representation of the binary('31', or 00000000000000000000000000110001, is the instruction to xor; 'db', or 00000000000000000000000011011011, is the address of the ebx register.  note that the first 24 leading zeros would probably be dropped in both cases, as 32-bit x86 machines will understand 16-bit or 8-bit x86 code just fine).  This is why assembly-to-binary is sometimes referred to as 'translation' rather than compilation.

---

### Post by the_darkside_986 on 2007-06-06
Sounds fun but not practical. It might be a great learning experience. I made a software called hexmk that takes a text file full of numbers and "compiles" it into a binary file. I got sick of trying to insert numbers in a hex editor for something I was working on (virtual machine byte code for RPG scripting language). The syntax for the text file is
```

1 2 3 4 // this will put the values 0x01 0x02 0x03 0x04 in binary form in the output file

```
And it supports short, long, and string values as well. If anyone wants to use it, I'll upload the source code somewhere. It's a simple tool I wrote in about 30 minutes but anyone attempting to produce raw binary files might like it.

Thanks for mentioning objdump whoever mentioned it. I didn't realize disassembling was so easy in Linux. I'm going to have lots of fun with this now. Linux pwns as a dev. platform.

---

### Post by willz06jw on 2007-06-06
Yea my experiment was meant to be pointless and stupid, but fun (for me)!  But if assembler is just about the same thing, and there is no way to directly program binary(again for fun!), I have only one other question:  What do you program assembler in, just VI?

Will

---

### Post by Extrudedaluminiu on 2007-06-06
You can use any text editor you like; you just need to use an assembler to assemble it to a binary. NASM and GAS are top choices.

Sidenote, you can't just write a file containing the opcodes for the instructions that you want to execute - there needs to be a binary header in place so that the OS can load the program. The build process will take care of that for you.

---

### Post by tenzindorje on 2007-06-06
Coding in assembler is machine dependent - Intel assembler won't work on PowerPC, for example. Also, coding for modern chips (Pentium, Dual Core) is far more difficult than coding for older chips (6502, 8086, 68000). It might be educational to try, but not practical.

To code as close to the metal as possible, I'd suggest C. It compiles to very fast machine code. To learn
programming, C is not as good a choice because it is not object-oriented, as modern languages such
as Java, C++, C#, and Ruby are. Java is a good language to learn, especially if you are interested in a career in computer programming. C# is not a particularly good choice for Linux. Ruby would be a good choice for several reasons - it's a clean, object-oriented language; it's current; it has practical applications (Ruby for Rails); and you don't need anything extra - just Ruby (which comes with Linux) and a text editor. All you have
to do is edit your program, save it, open a terminal, and type "ruby myprogram.rb".

---

