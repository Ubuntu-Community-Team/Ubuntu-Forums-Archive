---
title: "Need help with ELF machine code..."
date: 2007-01-04
forum: Programming Talk
---

### Post by Wybiral on 2007-01-04
Hey, I'm looking for some good references on the ELF file format... I need a decent list of the byte values that assembly opcodes get converted to. I'm trying to turn an interpretor I wrote into a compiler and I need to know what the byte equivalents would be for the command ASM opcodes like push/pup/add/sub... ect.

Any info will help, somewhere to start. I've searched all over the net for some references and have only found a little. I know a lot about the compiler side and the parsing, that's all covered, now I just need some info on the ELF file format and a conversion chart between opcodes and binary values.

Thanks!

EDIT:

I just realized I can figure a lot of it out by disassembling small test programs written in ASM, so I think I'll figure most of them out that way and probably gain a bit of knowledge on the ELF format. I would still like some good references if anyone has any... If not, I'll probably start a journal for people who run into this like me.

---

### Post by NicolásB on 2007-01-04
[http://www.wotsit.org/download.asp?f=elf11g](http://www.wotsit.org/download.asp?f=elf11g)

The opcodes should be in any x86 manual (same opcodes windows has, different interrupt vector).

Disclaimer: I haven't acctualy developed anything in linux-asm

---

### Post by Wybiral on 2007-01-04
Thanks, I found quite a bit of info in that site. I'm not 100% at my pentacle of understanding yet, but it's a pretty good start. I've since found a few more documents that are really helpful, and using objdump and hex editors I've found out a lot myself. When I understand more I'll post up some of my notes. From what I can tell, it shouldn't be hard to write an assembler at all!

---

### Post by Wybiral on 2007-01-04
Ok, in a highly reduced assembly program that essentially used these commands...

```

inc eax
mov eax, 1
int 0x80

```

Here is what the hex dump of the file looks like...

```

7f 45 4c 46 01 01 01 00 00 00 00 00 00 00 00 00 02 00 03 00 01 00 00 00 54 80
04 08 34 00 00 00 00 00 00 00 00 00 00 00 34 00 20 00 01 00 00 00 00 00 00 00
01 00 00 00 00 00 00 00 00 80 04 08 00 80 04 08 5c 00 00 00 5c 00 00 00 05 00
00 00 00 10 00 00 40 b8 01 00 00 00 cd 80

```

The final size of the file was 92 bytes... Notice the two 5c's? Those denote the file size in bytes (actually, it's the two "5c 00 00 00")

Now, adding an extra "inc eax" to the assembly code, like this...

```

inc eax
inc eax
mov eax, 1
int 0x80

```

Resulted in this...

```

7f 45 4c 46 01 01 01 00 00 00 00 00 00 00 00 00 02 00 03 00 01 00 00 00 54 80
04 08 34 00 00 00 00 00 00 00 00 00 00 00 34 00 20 00 01 00 00 00 00 00 00 00
01 00 00 00 00 00 00 00 00 80 04 08 00 80 04 08 5d 00 00 00 5d 00 00 00 05 00
00 00 00 10 00 00 40 40 b8 01 00 00 00 cd 80 

```

You can notice that not only did the 5c's change to 5d's (as a result of the extra byte) but after the "40" near the end of the file, there is another "40"

"40" is the byte that represents "inc eax"
"b8" is "mov eax" followed by a four byte value "01 00 00 00" which is the 1 in "mov eax, 1"

"cd" is "int" and "80" is... 80 (or "0x80")

I've done some other test's and I'm discovering this to be a very simple format. Apart from having to memorize the hex value for each command, I don't think it would be too hard to actually write executable ELF files in a hex editor! I'm aware that once I start getting into adding other sections to the file that it will become more difficult, but so far so good.

The first 16 bytes are the elf ID, the next two bytes denote that it's an executable, the next two denote that it's in intel  format.

BTW, if you're wondering what some practical uses for this kind of knowledge would be... You could shave a lot of useless space off of an executable if you know what to cut out, here is "Hello world!" in 125 bytes!

```

7f 45 4c 46 01 01 01 00 00 00 00 00 00 00 00 00 02 00 03 00 01 00 00 00 54 80
04 08 34 00 00 00 00 00 00 00 00 00 00 00 34 00 20 00 01 00 00 00 00 00 00 00
01 00 00 00 00 00 00 00 00 80 04 08 00 80 04 08 6d 00 00 00 6d 00 00 00 05 00
00 00 00 10 00 00 b8 04 00 00 00 bb 01 00 00 00 b9 71 80 04 08 ba 0c 00 00 00
cd 80 b8 01 00 00 00 cd 80 48 65 6c 6c 6f 20 77 6f 72 6c 64 21

```

---

### Post by pmasiar on 2007-01-04
I guess you checked [ELF]("http://en.wikipedia.org/wiki/Executable_and_Linkable_Format")  but just in case ...

---

### Post by Wybiral on 2007-01-06
*** Smacks head ***

I'm an idiot, there were a ton of improvements that could be made on that "Hello world!" program, here is as small as I could get it, at a whopping 96 bytes...

```

7f 45 4c 46 01 01 01 00 00 00 00 00 00 00 00 00 02 00 03 00 01 00 00 00 42 80
04 08 2c 00 00 00 00 00 00 00 00 00 00 00 2c 00 20 00 01 00 00 00 00 00 00 00
00 80 04 08 00 80 04 08 60 00 00 00 60 00 b0 04 b3 01 b9 53 80 04 08 b2 0d cd
80 b0 01 cd 80 48 65 6c 6c 6f 20 77 6f 72 6c 64 21 0a

```

But, so far that's the best I can do (It wont accept any headers with anything else cut out and the assembly is about as small as I can get it).

---

