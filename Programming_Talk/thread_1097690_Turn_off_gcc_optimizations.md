---
title: "Turn off gcc optimizations"
date: 2009-03-16
forum: Programming Talk
---

### Post by g3k0 on 2009-03-16
Hey,
Does anyone know how to turn off gcc optimizations?  I was reading some google sites but they were talking about both compiling and assembling.  I am just compiling with the -S option to get the assembly code it produces.
for instance in my C program I will multiply 7*5, is it possible to have it **not** put 35 in the assembly code automatically?

---

### Post by CptPicard on 2009-03-16
Try the -O0 flag

---

### Post by g3k0 on 2009-03-16
It still says 35
Here is my .c
```

void mulme(int num) {
	int a,b;
	a=5*7;
	b=2;  
}

```
Here is my .s
```

	.file	"test.c"
	.text
.globl mulme
	.type	mulme, @function
mulme:
	pushl	%ebp
	movl	%esp, %ebp
	subl	$16, %esp
	movl	$35, -4(%ebp)
	movl	$2, -8(%ebp)
	leave
	ret
	.size	mulme, .-mulme
	.ident	"GCC: (Ubuntu 4.3.2-1ubuntu12) 4.3.2"
	.section	.note.GNU-stack,"",@progbits

```
Variables aren't declared, 7 and 5 are multiplied :(  Maybe these optimizations are too basic to be removed?

---

### Post by Habbit on 2009-03-16
> **g3k0 said:**
> Variables aren't declared, 7 and 5 are multiplied :(  Maybe these optimizations are too basic to be removed?

Your "problem" is that gcc will resolve operations on compile-time constants whenever it sees them, and in particular an operation on two numbers is always expanded if it does not cause precision loss compared to the CPU-provided opcode.

You want to compile something like this **with -O0** just so gcc does not get any ideas:```
void mulme(int num) {
    int a = 5, b = 7;
    a *= b;
    b = 2;
}
```
```
        .file   "test.c"
        .text
.globl mulme
        .type   mulme, @function
mulme:
        pushl   %ebp
        movl    %esp, %ebp
        subl    $16, %esp
        movl    $5, -4(%ebp)
        movl    $7, -8(%ebp)
        movl    -4(%ebp), %eax
        imull   -8(%ebp), %eax
        movl    %eax, -4(%ebp)
        movl    $2, -8(%ebp)
        leave
        ret
        .size   mulme, .-mulme
        .ident  "GCC: (Ubuntu 4.3.2-1ubuntu12) 4.3.2"
        .section        .note.GNU-stack,"",@progbits

```

---

### Post by lloyd_b on 2009-03-16
I believe that it *is* too basic.  The compiler is seeing "5 * 7", and saying "I'll go ahead and do the math, and save some trouble at runtime".

What you could do instead is use some intermediate variables:```
int a,b;
int c = 5;
int d = 7;

a = c * d;
b = 7
```
With "-O0", this will actually force the program to do the "imull" to multiply them at runtime...

Lloyd B.

---

### Post by CptPicard on 2009-03-16
If you think of it, if you expected the literal multiplication expression to actually be broken up into two separate values in registers, the compiler would have to actually *introduce* those variables from nowhere, and that really is no longer a non-optimization but in a sense rewriting of the program...

---

