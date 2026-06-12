---
title: "GDT Protected Mode Programming"
date: 2012-06-28
forum: Programming Talk
---

### Post by leyley on 2012-06-28
I am trying to write a program that enter the protected mode and show a 'P', but it doesn't work. The code is shown below, anyone can solve this problem? Thanks
```

/* Boot file of nosdl;
 * This file is loaded at 0x8000;
 * Enter the protected mode and run init;
 * The max size of this file is 8k;
 */

#define BOOTSEG 0x8000	/* where I am in; */

/* Generate a gdt with 32bits base, 20bits limit and 12bits flag; 
 * We use a 32bits limit (low 20bits available) and
 * 16bits flag (lower 4bits of higher byte are always 0) here; 
 */

.text
.code16
.globl _start
_start:
	movl $0xB800,%eax
	movl %eax,%gs
	mov $'0',%al
	mov $0x0C,%ah
	movl %eax,%gs:((80*0+5)*2)
/* Prepare to enter the protected mode; */
__enter:
	/* Clear interrupt flags; */
	cli
	/* Load GDT; */
	lgdt gdtptr
	/* Reset registers; */
	movl $sel_kdata,%eax
	movl %eax,%ds
	movl %eax,%es
	movl %eax,%fs
	movl %eax,%gs
	/* Open A20 Line; */
	inb $0x92,%al
	orb $0b00000010,%al
	outb %al,$0x92
	/* Set cr0, enter protected mode; */
	movl %cr0,%eax
	orl $0x01,%eax
	movl %eax,%cr0
	ljmp $0x10,$(__enter32)
/*
 * Here we enter the 32bits world;
 * The next step is init idt and other things;
 */
__enter32:
.code32
	/* Display a P; */
	xorl %eax,%eax
	movl $sel_video,%eax
	movl %eax,%gs
	movl $((80*0+10)*2),%edi
	mov $0x0F,%ah
	mov $'P',%al
	movl %eax,%gs:(%edi)
	jmp .
/* GDT table; */
.code16
gdt: 		.quad 0x0000000000000000	/* Not used; */
gdt_kstack: .quad 0x00CF92000000FFFF	/* Reserved for kernel stack; 0x08; */
gdt_kcode:  .quad 0x00CF9A000000FFFF	/* Kernel code segment; 0x10; */
gdt_kdata:  .quad 0x00CF92000000FFFF	/* Kernel data segment; 0x18; */
gdt_ustack: .quad 0x00CFF2000000FFFF	/* Reserved for user stack; 0x20; */
gdt_ucode:  .quad 0x00CFFA000000FFFF	/* User code segment; 0x28; */
gdt_udata:  .quad 0x00CFF2000000FFFF	/* User data segment; 0x30; */
gdt_video:  .quad 0x00CFF200B800FFFF	/* Video buffer; 0x38; */
		    .quad 0x0000000000000000	/* Not used; */
.set gdtlen, (.-gdt)	/* GDT Length; */
gdtptr: 	.2byte (gdtlen-1)	/* GDT Limit; */
gdtbase:	.4byte gdt	/* GDT Base address; */
/* Selectors; */
.set sel_kcode, gdt_kcode-gdt
.set sel_kdata, gdt_kdata-gdt
.set sel_ucode, gdt_ucode-gdt
.set sel_udata, gdt_udata-gdt
.set sel_video, gdt_video-gdt

```

---

### Post by leyley on 2012-06-28
The development environment is consists of:
CentOS 6.2 (x86_64)
gcc 4.4.6
make 3.81
virtualbox 4.1.16 (Used to boot the floppy image)

---

### Post by the_unforgiven on 2012-06-28
Need to know more than just the code - how are you building it and trying to run it?
Can you please post your Makefile?

---

