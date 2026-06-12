---
title: "Compiling bkerndev on linux"
date: 2009-11-14
forum: Programming Talk
---

### Post by matmatmat on 2009-11-14
Has anyone managed to compile bkerndev on linux? I've made changes to start.asm:
```

; bkerndev - Bran's Kernel Development Tutorial

; By:   Brandon F. (friesenb@gmail.com)

; Desc: Kernel entry point, stack, and Interrupt Service Routines.

;

; Notes: No warranty expressed or implied. Use at own risk.

;

; This is the kernel's entry point. We could either call main here,

; or we can use this to setup the stack or other nice stuff, like

; perhaps setting up the GDT and segments. Please note that interrupts

; are disabled at this point: More on interrupts later!

[BITS 32]

global start

start:

    mov esp, _sys_stack     ; This points the stack to our new stack area

    jmp stublet



; This part MUST be 4byte aligned, so we solve that issue using 'ALIGN 4'

ALIGN 4

mboot:

    ; Multiboot macros to make a few lines later more readable

    MULTIBOOT_PAGE_ALIGN	equ 1<<0

    MULTIBOOT_MEMORY_INFO	equ 1<<1

    MULTIBOOT_AOUT_KLUDGE	equ 1<<16

    MULTIBOOT_HEADER_MAGIC	equ 0x1BADB002

    MULTIBOOT_HEADER_FLAGS	equ MULTIBOOT_PAGE_ALIGN | MULTIBOOT_MEMORY_INFO | MULTIBOOT_AOUT_KLUDGE

    MULTIBOOT_CHECKSUM	equ -(MULTIBOOT_HEADER_MAGIC + MULTIBOOT_HEADER_FLAGS)

    EXTERN code, bss, end



    ; This is the GRUB Multiboot header. A boot signature

    dd MULTIBOOT_HEADER_MAGIC

    dd MULTIBOOT_HEADER_FLAGS

    dd MULTIBOOT_CHECKSUM

    

    ; AOUT kludge - must be physical addresses. Make a note of these:

    ; The linker script fills in the data for these ones!

    dd mboot

    dd code

    dd bss

    dd end

    dd start



; This is an endless loop here. Make a note of this: Later on, we

; will insert an 'extern _main', followed by 'call _main', right

; before the 'jmp $'.

stublet:

    extern main

    call main

    jmp $



; This will set up our new segment registers. We need to do

; something special in order to set CS. We do what is called a

; far jump. A jump that includes a segment as well as an offset.

; This is declared in C as 'extern void gdt_flush();'

global _gdt_flush

extern gp

_gdt_flush:

    lgdt [gp]

    mov ax, 0x10

    mov ds, ax

    mov es, ax

    mov fs, ax

    mov gs, ax

    mov ss, ax

    jmp 0x08:flush2

flush2:

    ret



; Loads the IDT defined in '_idtp' into the processor.

; This is declared in C as 'extern void idt_load();'

global _idt_load

extern idtp

_idt_load:

    lidt [idtp]

    ret



; In just a few pages in this tutorial, we will add our Interrupt

; Service Routines (ISRs) right here!

global _isr0

global _isr1

global _isr2

global _isr3

global _isr4

global _isr5

global _isr6

global _isr7

global _isr8

global _isr9

global _isr10

global _isr11

global _isr12

global _isr13

global _isr14

global _isr15

global _isr16

global _isr17

global _isr18

global _isr19

global _isr20

global _isr21

global _isr22

global _isr23

global _isr24

global _isr25

global _isr26

global _isr27

global _isr28

global _isr29

global _isr30

global _isr31



;  0: Divide By Zero Exception

_isr0:

    cli

    push byte 0

    push byte 0

    jmp isr_common_stub



;  1: Debug Exception

_isr1:

    cli

    push byte 0

    push byte 1

    jmp isr_common_stub



;  2: Non Maskable Interrupt Exception

_isr2:

    cli

    push byte 0

    push byte 2

    jmp isr_common_stub



;  3: Int 3 Exception

_isr3:

    cli

    push byte 0

    push byte 3

    jmp isr_common_stub



;  4: INTO Exception

_isr4:

    cli

    push byte 0

    push byte 4

    jmp isr_common_stub



;  5: Out of Bounds Exception

_isr5:

    cli

    push byte 0

    push byte 5

    jmp isr_common_stub



;  6: Invalid Opcode Exception

_isr6:

    cli

    push byte 0

    push byte 6

    jmp isr_common_stub



;  7: Coprocessor Not Available Exception

_isr7:

    cli

    push byte 0

    push byte 7

    jmp isr_common_stub



;  8: Double Fault Exception (With Error Code!)

_isr8:

    cli

    push byte 8

    jmp isr_common_stub



;  9: Coprocessor Segment Overrun Exception

_isr9:

    cli

    push byte 0

    push byte 9

    jmp isr_common_stub



; 10: Bad TSS Exception (With Error Code!)

_isr10:

    cli

    push byte 10

    jmp isr_common_stub



; 11: Segment Not Present Exception (With Error Code!)

_isr11:

    cli

    push byte 11

    jmp isr_common_stub



; 12: Stack Fault Exception (With Error Code!)

_isr12:

    cli

    push byte 12

    jmp isr_common_stub



; 13: General Protection Fault Exception (With Error Code!)

_isr13:

    cli

    push byte 13

    jmp isr_common_stub



; 14: Page Fault Exception (With Error Code!)

_isr14:

    cli

    push byte 14

    jmp isr_common_stub



; 15: Reserved Exception

_isr15:

    cli

    push byte 0

    push byte 15

    jmp isr_common_stub



; 16: Floating Point Exception

_isr16:

    cli

    push byte 0

    push byte 16

    jmp isr_common_stub



; 17: Alignment Check Exception

_isr17:

    cli

    push byte 0

    push byte 17

    jmp isr_common_stub



; 18: Machine Check Exception

_isr18:

    cli

    push byte 0

    push byte 18

    jmp isr_common_stub



; 19: Reserved

_isr19:

    cli

    push byte 0

    push byte 19

    jmp isr_common_stub



; 20: Reserved

_isr20:

    cli

    push byte 0

    push byte 20

    jmp isr_common_stub



; 21: Reserved

_isr21:

    cli

    push byte 0

    push byte 21

    jmp isr_common_stub



; 22: Reserved

_isr22:

    cli

    push byte 0

    push byte 22

    jmp isr_common_stub



; 23: Reserved

_isr23:

    cli

    push byte 0

    push byte 23

    jmp isr_common_stub



; 24: Reserved

_isr24:

    cli

    push byte 0

    push byte 24

    jmp isr_common_stub



; 25: Reserved

_isr25:

    cli

    push byte 0

    push byte 25

    jmp isr_common_stub



; 26: Reserved

_isr26:

    cli

    push byte 0

    push byte 26

    jmp isr_common_stub



; 27: Reserved

_isr27:

    cli

    push byte 0

    push byte 27

    jmp isr_common_stub



; 28: Reserved

_isr28:

    cli

    push byte 0

    push byte 28

    jmp isr_common_stub



; 29: Reserved

_isr29:

    cli

    push byte 0

    push byte 29

    jmp isr_common_stub



; 30: Reserved

_isr30:

    cli

    push byte 0

    push byte 30

    jmp isr_common_stub



; 31: Reserved

_isr31:

    cli

    push byte 0

    push byte 31

    jmp isr_common_stub





; We call a C function in here. We need to let the assembler know

; that '_fault_handler' exists in another file

extern fault_handler



; This is our common ISR stub. It saves the processor state, sets

; up for kernel mode segments, calls the C-level fault handler,

; and finally restores the stack frame.

isr_common_stub:

    pusha

    push ds

    push es

    push fs

    push gs

    mov ax, 0x10

    mov ds, ax

    mov es, ax

    mov fs, ax

    mov gs, ax

    mov eax, esp

    push eax

    mov eax, fault_handler

    call eax

    pop eax

    pop gs

    pop fs

    pop es

    pop ds

    popa

    add esp, 8

    iret



global _irq0

global _irq1

global _irq2

global _irq3

global _irq4

global _irq5

global _irq6

global _irq7

global _irq8

global _irq9

global _irq10

global _irq11

global _irq12

global _irq13

global _irq14

global _irq15



; 32: IRQ0

_irq0:

    cli

    push byte 0

    push byte 32

    jmp irq_common_stub



; 33: IRQ1

_irq1:

    cli

    push byte 0

    push byte 33

    jmp irq_common_stub



; 34: IRQ2

_irq2:

    cli

    push byte 0

    push byte 34

    jmp irq_common_stub



; 35: IRQ3

_irq3:

    cli

    push byte 0

    push byte 35

    jmp irq_common_stub



; 36: IRQ4

_irq4:

    cli

    push byte 0

    push byte 36

    jmp irq_common_stub



; 37: IRQ5

_irq5:

    cli

    push byte 0

    push byte 37

    jmp irq_common_stub



; 38: IRQ6

_irq6:

    cli

    push byte 0

    push byte 38

    jmp irq_common_stub



; 39: IRQ7

_irq7:

    cli

    push byte 0

    push byte 39

    jmp irq_common_stub



; 40: IRQ8

_irq8:

    cli

    push byte 0

    push byte 40

    jmp irq_common_stub



; 41: IRQ9

_irq9:

    cli

    push byte 0

    push byte 41

    jmp irq_common_stub



; 42: IRQ10

_irq10:

    cli

    push byte 0

    push byte 42

    jmp irq_common_stub



; 43: IRQ11

_irq11:

    cli

    push byte 0

    push byte 43

    jmp irq_common_stub



; 44: IRQ12

_irq12:

    cli

    push byte 0

    push byte 44

    jmp irq_common_stub



; 45: IRQ13

_irq13:

    cli

    push byte 0

    push byte 45

    jmp irq_common_stub



; 46: IRQ14

_irq14:

    cli

    push byte 0

    push byte 46

    jmp irq_common_stub



; 47: IRQ15

_irq15:

    cli

    push byte 0

    push byte 47

    jmp irq_common_stub



extern irq_handler



irq_common_stub:

    pusha

    push ds

    push es

    push fs

    push gs



    mov ax, 0x10

    mov ds, ax

    mov es, ax

    mov fs, ax

    mov gs, ax

    mov eax, esp



    push eax

    mov eax, irq_handler

    call eax

    pop eax



    pop gs

    pop fs

    pop es

    pop ds

    popa

    add esp, 8

    iret



; Here is the definition of our BSS section. Right now, we'll use

; it just to store the stack. Remember that a stack actually grows

; downwards, so we declare the size of the data before declaring

; the identifier '_sys_stack'

SECTION .bss

    resb 8192               ; This reserves 8KBytes of memory here

_sys_stack:




```
& made a bash script:
```

#!/bin/bash
nasm -f elf -o start.o start.asm
gcc -Wall -O -fstrength-reduce -fomit-frame-pointer -finline-functions -nostdinc -fno-builtin -I./include -c -o main.o main.c

gcc -Wall -O -fstrength-reduce -fomit-frame-pointer -finline-functions -nostdinc -fno-builtin -I./include -c -o scrn.o scrn.c

gcc -Wall -O -fstrength-reduce -fomit-frame-pointer -finline-functions -nostdinc -fno-builtin -I./include -c -o gdt.o gdt.c

gcc -Wall -O -fstrength-reduce -fomit-frame-pointer -finline-functions -nostdinc -fno-builtin -I./include -c -o idt.o idt.c

gcc -Wall -O -fstrength-reduce -fomit-frame-pointer -finline-functions -nostdinc -fno-builtin -I./include -c -o isrs.o isrs.c

gcc -Wall -O -fstrength-reduce -fomit-frame-pointer -finline-functions -nostdinc -fno-builtin -I./include -c -o irq.o irq.c

gcc -Wall -O -fstrength-reduce -fomit-frame-pointer -finline-functions -nostdinc -fno-builtin -I./include -c -o timer.o timer.c

gcc -Wall -O -fstrength-reduce -fomit-frame-pointer -finline-functions -nostdinc -fno-builtin -I./include -c -o kb.o kb.c

ld -T link.ld -o kernel.bin start.o main.o scrn.o gdt.o idt.o isrs.o irq.o timer.o kb.o

sudo losetup /dev/loop0 dev_kernel_grub.img
sudo mount /dev/loop0 /mnt
sudo cp main.o /mnt/kernel
sudo umount /dev/loop0
sudo losetup -d /dev/loop0 

rm *.o

```
but I still get these errors:
```

[m@host Sources]$ ./build.sh 
main.c:49: warning: return type of ‘main’ is not ‘int’
main.c: In function ‘main’:
main.c:63: warning: pointer targets in passing argument 1 of ‘puts’ differ in signedness
./include/system.h:30: note: expected ‘unsigned char *’ but argument is of type ‘char *’
main.c:51: warning: unused variable ‘i’
scrn.c: In function ‘puts’:
scrn.c:144: warning: pointer targets in passing argument 1 of ‘strlen’ differ in signedness
./include/system.h:24: note: expected ‘const char *’ but argument is of type ‘unsigned char *’
gdt.c: In function ‘gdt_install’:
gdt.c:59: warning: assignment makes integer from pointer without a cast
idt.c: In function ‘idt_install’:
idt.c:56: warning: assignment makes integer from pointer without a cast
isrs.c:98: warning: pointer targets in initialization differ in signedness
isrs.c:99: warning: pointer targets in initialization differ in signedness
isrs.c:100: warning: pointer targets in initialization differ in signedness
isrs.c:101: warning: pointer targets in initialization differ in signedness
isrs.c:102: warning: pointer targets in initialization differ in signedness
isrs.c:103: warning: pointer targets in initialization differ in signedness
isrs.c:104: warning: pointer targets in initialization differ in signedness
isrs.c:105: warning: pointer targets in initialization differ in signedness
isrs.c:107: warning: pointer targets in initialization differ in signedness
isrs.c:108: warning: pointer targets in initialization differ in signedness
isrs.c:109: warning: pointer targets in initialization differ in signedness
isrs.c:110: warning: pointer targets in initialization differ in signedness
isrs.c:111: warning: pointer targets in initialization differ in signedness
isrs.c:112: warning: pointer targets in initialization differ in signedness
isrs.c:113: warning: pointer targets in initialization differ in signedness
isrs.c:114: warning: pointer targets in initialization differ in signedness
isrs.c:116: warning: pointer targets in initialization differ in signedness
isrs.c:117: warning: pointer targets in initialization differ in signedness
isrs.c:118: warning: pointer targets in initialization differ in signedness
isrs.c:119: warning: pointer targets in initialization differ in signedness
isrs.c:120: warning: pointer targets in initialization differ in signedness
isrs.c:121: warning: pointer targets in initialization differ in signedness
isrs.c:122: warning: pointer targets in initialization differ in signedness
isrs.c:123: warning: pointer targets in initialization differ in signedness
isrs.c:125: warning: pointer targets in initialization differ in signedness
isrs.c:126: warning: pointer targets in initialization differ in signedness
isrs.c:127: warning: pointer targets in initialization differ in signedness
isrs.c:128: warning: pointer targets in initialization differ in signedness
isrs.c:129: warning: pointer targets in initialization differ in signedness
isrs.c:130: warning: pointer targets in initialization differ in signedness
isrs.c:131: warning: pointer targets in initialization differ in signedness
isrs.c:133: warning: pointer targets in initialization differ in signedness
isrs.c: In function ‘fault_handler’:
isrs.c:146: warning: pointer targets in passing argument 1 of ‘puts’ differ in signedness
./include/system.h:30: note: expected ‘unsigned char *’ but argument is of type ‘char *’
timer.c: In function ‘timer_handler’:
timer.c:26: warning: pointer targets in passing argument 1 of ‘puts’ differ in signedness
./include/system.h:30: note: expected ‘unsigned char *’ but argument is of type ‘char *’
ld: warning: cannot find entry symbol start; defaulting to 00100000
gdt.o: In function `gdt_install':
gdt.c:(.text+0x10e): undefined reference to `gdt_flush'
idt.o: In function `idt_install':
idt.c:(.text+0x64): undefined reference to `idt_load'
isrs.o: In function `isrs_install':
isrs.c:(.text+0x48): undefined reference to `isr0'
isrs.c:(.text+0x6c): undefined reference to `isr1'
isrs.c:(.text+0x90): undefined reference to `isr2'
isrs.c:(.text+0xb4): undefined reference to `isr3'
isrs.c:(.text+0xd8): undefined reference to `isr4'
isrs.c:(.text+0xfc): undefined reference to `isr5'
isrs.c:(.text+0x120): undefined reference to `isr6'
isrs.c:(.text+0x144): undefined reference to `isr7'
isrs.c:(.text+0x168): undefined reference to `isr8'
isrs.c:(.text+0x18c): undefined reference to `isr9'
isrs.c:(.text+0x1b0): undefined reference to `isr10'
isrs.c:(.text+0x1d4): undefined reference to `isr11'
isrs.c:(.text+0x1f8): undefined reference to `isr12'
isrs.c:(.text+0x21c): undefined reference to `isr13'
isrs.c:(.text+0x240): undefined reference to `isr14'
isrs.c:(.text+0x264): undefined reference to `isr15'
isrs.c:(.text+0x288): undefined reference to `isr16'
isrs.c:(.text+0x2ac): undefined reference to `isr17'
isrs.c:(.text+0x2d0): undefined reference to `isr18'
isrs.c:(.text+0x2f4): undefined reference to `isr19'
isrs.c:(.text+0x318): undefined reference to `isr20'
isrs.c:(.text+0x33c): undefined reference to `isr21'
isrs.c:(.text+0x360): undefined reference to `isr22'
isrs.c:(.text+0x384): undefined reference to `isr23'
isrs.c:(.text+0x3a8): undefined reference to `isr24'
isrs.c:(.text+0x3cc): undefined reference to `isr25'
isrs.c:(.text+0x3f0): undefined reference to `isr26'
isrs.c:(.text+0x414): undefined reference to `isr27'
isrs.c:(.text+0x438): undefined reference to `isr28'
isrs.c:(.text+0x45c): undefined reference to `isr29'
isrs.c:(.text+0x480): undefined reference to `isr30'
isrs.c:(.text+0x4a4): undefined reference to `isr31'
irq.o: In function `irq_install':
irq.c:(.text+0x159): undefined reference to `irq0'
irq.c:(.text+0x17d): undefined reference to `irq1'
irq.c:(.text+0x1a1): undefined reference to `irq2'
irq.c:(.text+0x1c5): undefined reference to `irq3'
irq.c:(.text+0x1e9): undefined reference to `irq4'
irq.c:(.text+0x20d): undefined reference to `irq5'
irq.c:(.text+0x231): undefined reference to `irq6'
irq.c:(.text+0x255): undefined reference to `irq7'
irq.c:(.text+0x279): undefined reference to `irq8'
irq.c:(.text+0x29d): undefined reference to `irq9'
irq.c:(.text+0x2c1): undefined reference to `irq10'
irq.c:(.text+0x2e5): undefined reference to `irq11'
irq.c:(.text+0x309): undefined reference to `irq12'
irq.c:(.text+0x32d): undefined reference to `irq13'
irq.c:(.text+0x351): undefined reference to `irq14'
irq.c:(.text+0x375): undefined reference to `irq15'

```

---

