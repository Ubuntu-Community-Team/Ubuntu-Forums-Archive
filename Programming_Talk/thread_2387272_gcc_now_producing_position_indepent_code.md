---
title: "gcc now producing position indepent code?"
date: 2018-03-16
forum: Programming Talk
---

### Post by rplantz on 2018-03-16
I have a simple Hello world C program that uses write:

```

#include <unistd.h>
int main(void)
{

    write(STDOUT_FILENO, "Hello world.\n", 13);
  
    return 0;
}

```
When I last compiled it (5 years ago) it produced:

```

	.file	"helloWorld2.c"
	.section	.rodata
.LC0:
	.string	"Hello world.\n"  # constant data
	.text
	.globl	main
	.type	main, @function
main:
	pushq	%rbp
	movq	%rsp, %rbp
	movl	$13, %edx     # third argument
	movl	$.LC0, %esi   # second argument
	movl	$1, %edi      # first argument
	call	write
	movl	$0, %eax
	popq	%rbp
	ret
	.size	main, .-main
	.ident	"GCC: (Ubuntu/Linaro 4.7.0-7ubuntu3) 4.7.0"
	.section	.note.GNU-stack,"",@progbits

```

Now it produces:

```

	.file	"helloWorld2.c"
	.section	.rodata
.LC0:
	.string	"Hello world.\n"
	.text
	.globl	main
	.type	main, @function
main:
.LFB0:
	.cfi_startproc
	pushq	%rbp
	.cfi_def_cfa_offset 16
	.cfi_offset 6, -16
	movq	%rsp, %rbp
	.cfi_def_cfa_register 6
	movl	$13, %edx
	leaq	.LC0(%rip), %rsi
	movl	$1, %edi
	call	write@PLT
	movl	$0, %eax
	popq	%rbp
	.cfi_def_cfa 7, 8
	ret
	.cfi_endproc
.LFE0:
	.size	main, .-main
	.ident	"GCC: (Ubuntu 7.2.0-8ubuntu3.2) 7.2.0"
	.section	.note.GNU-stack,"",@progbits

```
When did gcc start producing PIC?

---

### Post by &amp;wP*!) on 2018-04-04
Which GCC versions did you use in both cases?
And which options were given to each compiler?
Was it a cross compilation?

---

### Post by rplantz on 2018-04-04
> **pencuse said:**
> Which GCC versions did you use in both cases?
The older compilation used gcc 4.7.0, the newer one 7.2.0. I'm not positive about the date of the older one, but it was 3 - 5 years ago.
> And which options were given to each compiler?
-S to get the assembly language and -O0 for no optimization. I may have also used -g to get debugging symbols.
> Was it a cross compilation? No.

I have read elsewhere that Ubuntu started using Address Space Layout Randomization (ASLR) with the 16.10 release. If I'm understanding things correctly, that means that the default became position independent code.

---

### Post by &amp;wP*!) on 2018-04-08
To find out whether your GCC compiler also has this default setting, type: **gcc -v** and search whether the option **--enable-default-pie** is there. If this option is in the stderr of gcc -v, then yes, all your object files coming from gcc -o <object file> are position-independent code. 

I confirm what you say: because of ASLR (security reasons) almost all OSes have GCC with PIC enabled.

---

