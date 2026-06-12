---
title: "distorm disassembly correct?"
date: 2008-11-28
forum: Programming Talk
---

### Post by WitchCraft on 2008-11-28
Hi, I'm currently testing distrom disassembler...

Now, it seems like the output is incorrect, or is that wrong:

If I disassemble VM_Create with gdb, i get a correct disassembly:
```

 disas VM_Create
Dump of assembler code for function VM_Create:
0x080b95d8 <VM_Create+0>:	sub    $0x2c,%esp
0x080b95db <VM_Create+3>:	mov    %esi,0x20(%esp)
0x080b95df <VM_Create+7>:	mov    0x30(%esp),%esi
0x080b95e3 <VM_Create+11>:	mov    %edi,0x24(%esp)
0x080b95e7 <VM_Create+15>:	mov    0x38(%esp),%edi
0x080b95eb <VM_Create+19>:	test   %esi,%esi
0x080b95ed <VM_Create+21>:	mov    %ebx,0x1c(%esp)
0x080b95f1 <VM_Create+25>:	mov    %ebp,0x28(%esp)
0x080b95f5 <VM_Create+29>:	je     0x80b981e <VM_Create+582>
0x080b95fb <VM_Create+35>:	cmpb   $0x0,(%esi)
0x080b95fe <VM_Create+38>:	je     0x80b981e <VM_Create+582>
0x080b9604 <VM_Create+44>:	mov    0x34(%esp),%eax
0x080b9608 <VM_Create+48>:	test   %eax,%eax
0x080b960a <VM_Create+50>:	je     0x80b981e <VM_Create+582>
0x080b9610 <VM_Create+56>:	call   0x807d750 <Hunk_MemoryRemaining>
0x080b9615 <VM_Create+61>:	mov    %esi,0x4(%esp)
0x080b9619 <VM_Create+65>:	mov    %eax,%ebp

```

if I use distorm:
 ./disasm openarena.i386 80b95d8 >> te.txt
```

diStorm version: 1.7.30
bits: 32
filename: openarena.i386
origin: 080b95d8
080b95d8 (02) 7f 45                    JG 0x80b961f
080b95da (01) 4c                       DEC ESP
080b95db (01) 46                       INC ESI
080b95dc (02) 0101                     ADD [ECX], EAX
080b95de (02) 0100                     ADD [EAX], EAX
080b95e0 (02) 0000                     ADD [EAX], AL
080b95e2 (02) 0000                     ADD [EAX], AL
080b95e4 (02) 0000                     ADD [EAX], AL
080b95e6 (02) 0000                     ADD [EAX], AL
080b95e8 (02) 0200                     ADD AL, [EAX]
080b95ea (02) 0300                     ADD EAX, [EAX]
080b95ec (02) 0100                     ADD [EAX], EAX
080b95ee (02) 0000                     ADD [EAX], AL
080b95f0 (07) 80ba 04083400 00         CMP BYTE [EDX+0x340804], 0x0
080b95f7 (03) 0068 58                  ADD [EAX+0x58], CH
080b95fa (01) 16                       PUSH SS
080b95fb (02) 0000                     ADD [EAX], AL
080b95fd (02) 0000                     ADD [EAX], AL
080b95ff (03) 003400                   ADD [EAX+EAX], DH
080b9602 (02) 2000                     AND [EAX], AL
080b9604 (01) 07                       POP ES
080b9605 (02) 0028                     ADD [EAX], CH
080b9607 (02) 0021                     ADD [ECX], AH
080b9609 (02) 001e                     ADD [ESI], BL
080b960b (02) 0006                     ADD [ESI], AL
080b960d (02) 0000                     ADD [EAX], AL
080b960f (03) 003400                   ADD [EAX+EAX], DH
080b9612 (02) 0000                     ADD [EAX], AL
080b9614 (02) 34 80                    XOR AL, 0x80
080b9616 (02) 04 08                    ADD AL, 0x8

```

Doesn't look correct, or not?

---

### Post by happysmileman on 2008-11-28
> **WitchCraft said:**
> 
Doesn't look correct, or not?

Don't have much experience with assembler, but no, it looks completely different in every way.

The second one basically just looks like a load of "ADD [EAX], AL"s everywhere, mixed in with occassionally something different.

```
080b95e0 (02) 0000                     ADD [EAX], AL
080b95e2 (02) 0000                     ADD [EAX], AL
080b95e4 (02) 0000                     ADD [EAX], AL
080b95e6 (02) 0000                     ADD [EAX], AL
080b95e8 (02) 0200                     ADD AL, [EAX]
080b95ea (02) 0300                     ADD EAX, [EAX]
080b95ec (02) 0100                     ADD [EAX], EAX
080b95ee (02) 0000                     ADD [EAX], AL

```

I don't think that would ever serve a purpose anywhere.

---

### Post by WitchCraft on 2008-11-28
> **happysmileman said:**
> Don't have much experience with assembler, but no, it looks completely different in every way.

The second one basically just looks like a load of "ADD [EAX], AL"s everywhere, mixed in with occassionally something different.

```
080b95e0 (02) 0000                     ADD [EAX], AL
080b95e2 (02) 0000                     ADD [EAX], AL
080b95e4 (02) 0000                     ADD [EAX], AL
080b95e6 (02) 0000                     ADD [EAX], AL
080b95e8 (02) 0200                     ADD AL, [EAX]
080b95ea (02) 0300                     ADD EAX, [EAX]
080b95ec (02) 0100                     ADD [EAX], EAX
080b95ee (02) 0000                     ADD [EAX], AL

```

I don't think that would ever serve a purpose anywhere.

yea, think so, too...:lolflag:

---

### Post by WitchCraft on 2008-11-29
bump. diStrom sucks. Is there anything that I might have done wrong?

---

### Post by NathanB on 2008-11-29
This is easy to explain...

When you tell gdb to disassemble a function, gdb shows what that function looks like in memory -- all of it is machine code representing that function.  No metadata.  No embedded symbols.

When you tell diStorm to disassemble an executable, it accesses the entire file from disk -- this includes lots of metadata such as the file header, initialized data sections, un-initialized data sections, symbol data, etc.

You should study the executable file formats to discover the offset at which the code is stored:

[http://www.wotsit.org/list.asp?fc=5](http://www.wotsit.org/list.asp?fc=5)

Until you learn how to use command-line tools, you might want to stay with GUI-based ones:

[http://freshmeat.net/projects/edebugger/](http://freshmeat.net/projects/edebugger/)
[http://www.ollydbg.de/](http://www.ollydbg.de/)

---

### Post by WitchCraft on 2008-12-05
> **NathanB said:**
> This is easy to explain...

When you tell gdb to disassemble a function, gdb shows what that function looks like in memory -- all of it is machine code representing that function.  No metadata.  No embedded symbols.

When you tell diStorm to disassemble an executable, it accesses the entire file from disk -- this includes lots of metadata such as the file header, initialized data sections, un-initialized data sections, symbol data, etc.

You should study the executable file formats to discover the offset at which the code is stored:

[http://www.wotsit.org/list.asp?fc=5](http://www.wotsit.org/list.asp?fc=5)

Until you learn how to use command-line tools, you might want to stay with GUI-based ones:

[http://freshmeat.net/projects/edebugger/](http://freshmeat.net/projects/edebugger/)
[http://www.ollydbg.de/](http://www.ollydbg.de/)

which is why i gave it the offset to the function... but obviously that's not the same...

---

### Post by WitchCraft on 2008-12-11
OK, i had a closer look on it on objdump and hexedit.

Now I obviously have to get the disassembly starting from the .text section till the end of the .text section (and cross reference the strings from the other sections)...

Now the thing is that i need to subtract 0x804000 or something like this (wrote it down, but don't find the paper atm) from the offset obtained from nm to get the position of the desired function in the file (hexdump).

Now, at this position in the file starts exactly the function i was inspecting. I gave the new offset to distrom, but again seems to be plain wrong. 

I've tried another x86 instruction set decoder than distorm, which seems to give a correct disassembly so far, but in the mid of the first function starts screwing up (error in the decoder, probably only 386 decoder, and i have 686 code)

Anywhere a good (=working) decoder (x86 & x86_64)?

---

### Post by NathanB on 2008-12-13
Get Agner's object file converter:

[http://www.agner.org/optimize/#objconv](http://www.agner.org/optimize/#objconv)

Inside "objconv.zip" is a Windows binary -- ignore this...

Open the included "source.zip" and run the "build.sh" script.

Now, a useful disassembly is as easy as:

$ objconv -fnasm Hello Hello.dis

..or even..

$ objconv -fnasm Hello.o Hello.dis

---

### Post by WitchCraft on 2008-12-14
> **NathanB said:**
> Get Agner's object file converter:

[http://www.agner.org/optimize/#objconv](http://www.agner.org/optimize/#objconv)

Inside "objconv.zip" is a Windows binary -- ignore this...

Open the included "source.zip" and run the "build.sh" script.

Now, a useful disassembly is as easy as:

$ objconv -fnasm Hello Hello.dis

..or even..

$ objconv -fnasm Hello.o Hello.dis

In the mean time I have started writing my own disassembler...
Already fully decodes 386+ & 3Dnow instruction set flawlessly, but I'm still fighting with SSE and x64

But: OMG, fantastic tool!!! It works! I'll immediately steal the macho.c to get mac support for my disassembler.

And I like the opcode map. This is almost identical to what I was doing, unlike gdb's and diStorms table.

And I like the idea of converting the file format, never thougt of it before, but it's a very interesting idea.

In case anybody is interested:
[http://www.c-jump.com/CIS77/CPU/x86/index.html](http://www.c-jump.com/CIS77/CPU/x86/index.html)

---

