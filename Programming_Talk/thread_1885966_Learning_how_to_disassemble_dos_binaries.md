---
title: "Learning how to disassemble dos binaries"
date: 2011-11-24
forum: Programming Talk
---

### Post by kerryhall on 2011-11-24
I was wondering how to get started either disassembling or decompiling DOS binaries. For example, let's try the doom shareware edition, which is free to download here: [http://www.doomworld.com/idgames/index.php?id=7043](http://www.doomworld.com/idgames/index.php?id=7043)

(Doom also had the source released, but I'm just interested in learning about x86 asm) 

So what is the standard entry point for a dos executable? Or is the entry point a value in the header? What would be a command to issue to x86dis to produce useful output, or should I use a different disassembler, like ndisasm? 

I was wondering if I could run the exe in dosbox, and have dosbox log the address of each instruction, and then produce some sort of file that shows exactly what instructions were executed, then compare that to x86dis or nasm output?

I guess my end goal here would be some simple graphics tweaks or similar. Maybe swap the R and the B when generating the palette? I might not even have to modify addresses of jumps if I do that. However, I would also like to do something that would require modifying the addresses. Maybe when I select an item in the menu, it jumps to my code which prints out a message to the console or something like that, then jumps back to where it was before.

Thanks!

---

### Post by An Sanct on 2011-11-24
I guess, with this question, you are here in for a *little* wait :)

Well, to mod graphic things, check out the WAD files, those are the compressed graphics, levels, animations, .... well the cog, that makes DOOM move...

As for x86 or ASM, A86, to be more specific, you should not seek the answer in a game, since games and other guerrilla software those times where moded. They where moded in a way, that is "not acceptable" anymore, crunched, compacted, compressed, squezzed, UPXed (,.....) and then cyphered, encrypted, "protected" and XORed (in any random order) .... you name it.

If actual DOS executables disassembly is the thing you are searching for, then search for disassemblers, that can handle the MZ *magic* [$4D 5A] (the default DOS 16bit header) or elf, coff, xcoff, ecoff, mach and such ...

Whatever it was, 640kb or 637kb, you decide ...it aught to be enough memory for anybody [(link here)]("http://en.wikiquote.org/wiki/Talk:Bill_Gates") ... so DOS executables use that space ... "PE" is the portable alternative to that, but this is a Windows thing... (my personal note here is, that you could pack a DOS command line executable *with* a Windows GUI application in the same EXE - so instead of it telling you "this is a windows application and cannot run in DOS", that was the normal PE stub "excuse" for Windows GUI compilers, you got functionality!)

Well, I'm kinda tired now, cannot help you further (at the moment ...). But if you want to study assembler, go with the 32bit, its time-relevant and helps you be a good programmer, keeping in mind, that *Small Is Beautiful* (I have all of 'em, you find your link yourself!).

well, as a bye for today, I will say this: If you spray 100g of salt (Na-Cl) on a cloud, it vanishes immediately.

Enyojz!

---

### Post by kerryhall on 2011-11-24
I know about modding doom with all the tools that are available, but my goal here is learning how to disassemble dos binaries. Hmm, so binaries from those days would decompress themselves? I wonder if dosbox would be the best tool to use then. Does dosbox load the whole thing in memory? I wonder if I could use dosbox to have the program decompress itself, then write a debug function in dosbox to dump the whole thing to an assembly file. Maybe I'll go ask over at the dosbox forums. 

Thanks!

---

### Post by pbrane on 2011-11-24
objdump can disassemble MZ and PE executable files if you use the mingw version.
Something like...
```

objdump
       -d                 # Disassembly only code
       -T                 # Dynamic symbol table
       -x                 # All header informations
       --prefix-addresses # Complete address
       --show-raw-insn    # Opcode bytes
       -C'                # Decode low-level-symbols (e.g. C++)
       -Mintel

       <executable name>

```

Should work

---

### Post by An Sanct on 2011-11-25
> **kerryhall said:**
> I know about modding doom with all the tools that are available, but my goal here is learning how to disassemble dos binaries. Hmm, so binaries from those days would decompress themselves? I wonder if dosbox would be the best tool to use then. Does dosbox load the whole thing in memory? I wonder if I could use dosbox to have the program decompress itself, then write a debug function in dosbox to dump the whole thing to an assembly file. Maybe I'll go ask over at the dosbox forums. 

Thanks!

I did not say they are always compressed. :) Sometimes, they are, sometimes, they aren't - You just have to analyze the executable and if needed, unpack it.

But it is true, that the code loads itself into memory at one point and that is when you need to dump the assembled binary and then disassemble it.

PS. I feel, that there is a more than 80% chance, that what I would write would get misinterpreted again, so I will just point you to a cool pages, that cover this topic.

[Reversing hints]("http://rewiki.regengedanken.de/wiki/Reverse_engineering_hints")
[An interesting forum entry]("http://forums.whirlpool.net.au/archive/880410")
[PEExplorer]("http://www.heaventools.com/PE_Explorer_disassembler.htm")
[Obj2ASM]("http://www.digitalmars.com/ctg/obj2asm.html")
[IDA (Hex Rays)]("http://www.hex-rays.com/products/ida/index.shtml")
[A wiki about disassemblers etc...]("http://en.wikibooks.org/wiki/X86_Disassembly/Disassemblers_and_Decompilers")

---

### Post by kerryhall on 2011-12-01
> **An Sanct said:**
> I did not say they are always compressed. :) Sometimes, they are, sometimes, they aren't - You just have to analyze the executable and if needed, unpack it.

But it is true, that the code loads itself into memory at one point and that is when you need to dump the assembled binary and then disassemble it.

PS. I feel, that there is a more than 80% chance, that what I would write would get misinterpreted again, so I will just point you to a cool pages, that cover this topic.

[Reversing hints]("http://rewiki.regengedanken.de/wiki/Reverse_engineering_hints")
[An interesting forum entry]("http://forums.whirlpool.net.au/archive/880410")
[PEExplorer]("http://www.heaventools.com/PE_Explorer_disassembler.htm")
[Obj2ASM]("http://www.digitalmars.com/ctg/obj2asm.html")
[IDA (Hex Rays)]("http://www.hex-rays.com/products/ida/index.shtml")
[A wiki about disassemblers etc...]("http://en.wikibooks.org/wiki/X86_Disassembly/Disassemblers_and_Decompilers")

Oh yeah, I didn't assume they are *always* compressed, but since it is somewhat likely, I would just like to assume it would be.

I found most of those links in my googling before asking here, but the problem is that they all require windows based tools.

Cheers!

---

### Post by 11jmb on 2011-12-01
Why not start out with the code and then compile it, but not assemble or link (-S flag in gcc)? It is easier, cleaner, and unquestionably legal.

---

### Post by lkraemer on 2011-12-23
kerryhall,
I have an old copy of Sourcer by V Communications and I can process
your file if you send me the Type Assembler you want for the Target.
Target Assembler Choices:
MASM-5.1
MASM-5.0
MASM-4.0
TASM-2.0
TASM-1.0
OPTASM
OTHER
NONE


I also need the CPU type, and Co-Processor type (or NONE) you want to target.
CPU & Math Co-Processor Choices
8086/8088	Math	8087	or NONE
V20/V30		Math	8087	or NONE
80186/80188	Math	8087	or NONE
286 Real	Math	80287	or NONE
286 Protected	Math	80287	or NONE
386 Real	Math	80387	or NONE
386 Protected	Math	80387	or NONE
486 Real	Math	80486	or NONE
486 Protected	Math	80486	or NONE


I'm attaching four photo's so you have an idea of what I'm talking about.

Maybe this will help with some of the information you are looking for.
You can always try to re-assemble the code and see if it executes.

PM me!

Enjoy!

lk

---

