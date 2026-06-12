---
title: "Error &quot;No rule to make 'XXX. Bin', stop&quot; when using make to make bin file"
date: 2023-02-01
forum: Packaging and Compiling Programs
---

### Post by 1z2j3p4h on 2023-02-01
System: Ubuntu 22.10
What need to installed to solve this problem?

---

### Post by monkeybrain20122 on 2023-02-01
Wow, can you give more details? It is like going to the doctor and say hey I am not feeling well can you help.

---

### Post by 1z2j3p4h on 2023-02-01
At that time, I was using vscode to write a program, and I needed to use make to make a bin file. It was normal when I made the.o file before, but this time I reported an error.
I guess Ubuntu is missing something.

---

### Post by monkeybrain20122 on 2023-02-01
First of all you didn't really provide anymore useful info such as your build log. No rule to make can be due to many things, maybe a bug in your program. 

Secondly it is bad form to ask for help in PM  (it maybe against forum rules though I am not sure) because other people may find the solution useful if they encounter similar problems in the future.

---

### Post by 1z2j3p4h on 2023-02-01
These are my codes.
```

----------kernel.cpp----------
void printf(char* str) {
    unsigned short* VideoMemory = (unsigned short*)0xb8000;
    for (int i = 0; str[i]; i++) {
        VideoMemory[i] = (VideoMemory[i] & 0xFF00) | str[i];
    }
}
extern "C" void kernelMain(void* multiboot_structure, unsigned int magicnumber) {
    printf("code name:freedom");
    while(1);
}


----------makefile----------
GPPPARAMS = -m32 -fno-user-cxa-atexit -fleading-underscore -fno-exceptions -fno-builtin -nostdlib -fno-rtti
ASPARAMS = --32
LDPARAMS = -melf_i386

objects = loader.o kernel.objects

%.o: %.cpp
    g++ ${GPPPARAMS} -o $@ -c $<

%.o: %.s
    as ${ASPARAMS} -o $@ $<

mykernel.bin: linker.ld ${objects}
    ld ${LDPARAMS} -T $< -o $@ ${objects}

install: mykernel.bin
    sudo cp $< /boot/mykernel.bin

----------loader.s----------
.set MAGIC, 0x1badb002
.set FLAGS, (1<<0 | 1<<1)
.set CHECKSUM, -(MAGIC + FLAGS)

.section .multboot
  .long MAGIC
  .long FLAGS
  .long CHECKSUM

.section .text
.extern kernelMain
.global loader



loader:
  mov $kernel_stack, %esp
  push %rax
  push %rbx
  call kernelMain

_stop:
  cli
  hlt
  jmp _stop

.section .bss
.space 2*1024*1024
kernel_stack:

----------linker.ld----------
ENTRY(loader)
OUTPUT_FORMAT(elf32-i386)
OUTPUT_ARCH(i386:i386)


SECTIONS 
{
    . - 0x0100000;
    .text :
    {
        *(.multiboot)
        *(.text*)
        *(.rodata)
    }


    .data :
    {
        start_ctors = .;
        KEEP(*(.init_array));
        KEEP(*(SORT_BY_INIT_PRIORITY(.init_array.*)));
        end_ctors = .;
        *(.data)
    }
    .bss :
    {
        *(.bss)
    }
    /DISCARD :
    {
        *(.fini_array*)
        *(.comment)
    }
}

```

---

### Post by 1z2j3p4h on 2023-02-01
For some reasons, the code display may be incorrect (such as incorrect indentation, etc.), please understand.

---

