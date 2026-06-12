---
title: "Undefined reference to kmain despite giving reference ( C )"
date: 2013-01-30
forum: Programming Talk
---

### Post by Jamie_Edwards on 2013-01-30
Hi guys,

Before I upgraded from Ubuntu 12.04 to 12.10 I didn't have this problem and also before I scrapped my last O.S. project I didn't have it either, anyway...

OK, here's my problem the compiler is giving me the following error:

```

S$ make
nasm -felf core/arch/boot.asm -o obj/boot.o
Completed all .asm files
ld -Tlink.ld -melf_i386  -o kern/kernel obj/boot.o
obj/boot.o: In function `start':
core/arch/boot.asm:(.__mbHeader+0x24): undefined reference to `_kmain'
make: *** [kern/kernel] Error 1

```

What that's telling me is my kmain function ( which is the kernel entry point ) isn't defined... But it is... and this is also a linker error as I have two .o files for both "main.c" and "boot.asm".

Also I tried the whole "_kmain" thing with "-fno-leading-underscores" make parameter too with the same results. Any ideas?

main.c:
```

#include <system.h>


void kmain( struct multiboot *mbd, unsigned int magic )
{
    return 0xDEADBEEF;
}

```

boot.asm:
```
; boot.asm -- The bootstrap for GRUB

; The Multiboot macroes for telling GRUB how to load the kernel

section .__mbHeader

MBOOT_PAGE_ALIGN        equ         1<<0                        ; Load everything on a page boundary
MBOOT_MEM_INFO          equ         1<<1                        ; Provide the kernel with the memory map
MBOOT_HEADER_MAGIC      equ         0x1BADB002                  ; Multiboot magic number, required by GRUB

MBOOT_HEADER_FLAGS      equ         MBOOT_PAGE_ALIGN | MBOOT_MEM_INFO
MBOOT_CHECKSUM          equ         -(MBOOT_HEADER_MAGIC + MBOOT_HEADER_FLAGS)


[bits 32]

[global mboot]
[extern code]
[extern bss]
[extern end]

mboot:
    dd  MBOOT_HEADER_MAGIC
    dd  MBOOT_HEADER_FLAGS
    dd  MBOOT_CHECKSUM

    dd  mboot
    dd  code
    dd  bss
    dd  end
    dd  start

[global start]
[extern _kmain]

start:
    push    esp
    push    ebx

    cli
    call    _kmain
    jmp     $

```

link.ld ( linker script ):
```

ENTRY(start)
OUTPUT_FORMAT(elf32-i386)

phys = 0x00100000;
SECTIONS
{
/*Set the virtual address:*/
. = phys;
/*
* http://wiki.osdev.org/Grub_Error_13
*/

/* .__mbHeader will begin @ 'phys' */
.__mbHeader : AT ( ADDR( .__mbHeader ) ) {
/* mboot = .;*/
*(.__mbHeader)
}

.text ALIGN(4096) : AT(ADDR(.text)) {
code = .;
*(.text)
*(.rodata)
}
.data ALIGN(4096) : AT(ADDR(.data)) /*Voila*/
{
data = .;
*(.data)
}
.bss ALIGN(4096) : AT ( ADDR (.bss) )
{
bss = .;
*(.bss)
}
end = .;
}

```

Thanks

---

