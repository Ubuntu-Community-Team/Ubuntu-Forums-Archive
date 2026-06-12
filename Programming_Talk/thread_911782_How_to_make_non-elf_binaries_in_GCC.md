---
title: "How to make non-elf binaries in GCC?"
date: 2008-09-06
forum: Programming Talk
---

### Post by paukku92 on 2008-09-06
I am making a little operating system. I have managed to make a bootloader etc. Now I'm trying to link together some assembler and C code. The only problem is that GCC makes ELF binaries. Is there any way to make non-ELF binaries with GCC?

---

### Post by paukku92 on 2008-09-06
I have managed to take off the elf headers etc. off with objcopy.

But why there is so much zeros between the data and the code

```
00000000   8D 4C 24 04  83 E4 F0 FF  71 FC 55 89  E5 51 66 8D  .L$.....q.U..Qf.
00000010   35 E0 0C 05  08 E8 06 00  00 00 59 5D  8D 61 FC C3  5.........Y].a..
00000020   B4 0E EB 00  67 8A 04 3C  00 74 06 CD  10 66 46 EB  ....g..<.t...fF.
00000030   F3 C3 8A 25  00 00 00 00  CD 16 C3 00  00 00 00 00  ...%............
00000040   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
00000050   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
00000060   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................

--snip--

00008C10   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
00008C20   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
00008C30   00 00 00 00  00 00 00 00  00 00 00 00  00 00 00 00  ................
00008C40   00 00 00 00  00 00 00 00  00 00 00 00  48 65 6C 6C  ............Hell
00008C50   6F 20 57 6F  72 6C 64 00  00 00 00 00  6C 6F 6F 70  o World.....loop
00008C60   20 65 6E 64  65 64 21 00  48 65 6C 6C  6F 20 54 68   ended!.Hello Th
00008C70   69 73 20 69  73 20 4D 79  20 46 69 72  73 74 20 42  is is My First B
00008C80   6F 6F 74 20  50 72 6F 67  72 61 6D 21  00           oot Program!.
00008C90



```

---

### Post by slavik on 2008-09-06
it has to do with libc I think. old version (2 or 3) still had the flat a.out type of thing. libc v6 is the latest used version

---

### Post by paukku92 on 2008-09-07
I don't think it is a libc issue, because just using gas (gnu assembler) produces also a lot of empty space in the middle of the executable. But when I used nasm there was no problem.

I would really like to use a c compiler with an assembler, how can I make the data and code to be closer together?

I am not forced to use gcc and gas, so any c compiler and assembler that work together are OK.

---

### Post by snova on 2008-09-07
> it has to do with libc I think. old version (2 or 3) still had the flat a.out type of thing. libc v6 is the latest used version

If libc is being linked in, you're already off track.

> Is there any way to make non-ELF binaries with GCC?

I humbly suggest you do not bother. It's a lot easier just to use standard tools and exe formats than it is to deal with binary blobs. Just put Grub on a floppy and use that. It even does filesystems- it's much simpler.

But if you insist on doing it the hard way (and honestly, it's hard for no reason), then what you want is a linker script. I don't remember how to write one, the one I use hasn't changed much since I began writing kernels. But up at the top, you'll want:

```
OUTPUT_FORMAT( "binary" )
```

Or something very close to this, at least.

Have fun.

---

### Post by jinksys on 2008-09-07
GCC doesn't make elf executables, by default the LD linker does.  GCC makes an object file and passes that on to LD.  I believe what you want to accomplish is have GCC compile your code, but have LD link a flat binary.

Here's how I compile my kernel:

```

as -o loader.o loader.s
gcc -o kernel.o -c kernel.c -Wall -Wextra -nostdlib -nostartfiles -nodefaultlibs -nostdinc -ffreestanding
gcc -o video.o -c video.c -Wall -Wextra -nostdlib -nostartfiles -nodefaultlibs -nostdinc -ffreestanding
gcc -o system.o -c system.c -Wall -Wextra -nostdlib -nostartfiles -nodefaultlibs -nostdinc -ffreestanding
gcc -o gdt.o -c gdt.c -Wall -Wextra -nostdlib -nostartfiles -nodefaultlibs -nostdinc -ffreestanding
gcc -o idt.o -c idt.c -Wall -Wextra -nostdlib -nostartfiles -nodefaultlibs -nostdinc -ffreestanding
ld -T linker.ld -o kernel.bin loader.o kernel.o video.o system.o gdt.o idt.o

```

My linker.ld:

```

ENTRY (_loader)

SECTIONS{
    . = 0x00100000;

    .text :{
        *(.text)
    }

    .rodata ALIGN (0x1000) : {
        *(.rodata)
    }

    .data ALIGN (0x1000) : {
        *(.data)
    }

    .bss : {
        _sbss = .;
        *(COMMON)
        *(.bss)
        _ebss = .;
    }
}
```

My kernel is actually a 32bit ELF since I load my kernel with GRUB, but if you want LD to spit out a binary just use the "--oformat binary" option when linking.

---

