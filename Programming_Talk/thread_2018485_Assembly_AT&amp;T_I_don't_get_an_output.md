---
title: "Assembly AT&amp;T: I don't get an output???"
date: 2012-07-06
forum: Programming Talk
---

### Post by zapperterrus on 2012-07-06
This is the code:

```

.data
.text
.globl _start
_start:
mov $56, %ax
mov $4, %bx
add %ax, %bx
push %ax
call printf
pop %ax
fine:
mov $1, %eax
int $0x80

```

And this is that i did with terminal:
```

$ as -o prova.o prova.s
$ ld -dynamic-linker /lib/ld-linux.so.2 -lc -o prova prova.o
$ ./prova
$ 

```

---

### Post by xb12x on 2012-07-06
Here is a method to see how to call a 'C' library routine from an assembly file. I am not suggesting you cut and paste from the myprint.s file, but instead use it to see the registers required for the call, and the correct stack handling.

1. Create a 'C' file that calls the particular 'C' library routine:


```
// myprint.c

#include <stdio.h>

#define NUM 60

int main(int argc, char **argv)
{
    printf("hello world\n");
    return 0;
}
```


2. compile to a 32bit assembly file named myprint.s:
gcc -m32 -S myprint.c


3. View myprint.s with a text editor:

```

	.file	"myprint.c"
	.section	.rodata
.LC0:
	.string	"%d\n"
	.text
	.globl	main
	.type	main, @function
main:
.LFB0:
	.cfi_startproc
	pushl	%ebp
	.cfi_def_cfa_offset 8
	.cfi_offset 5, -8
	movl	%esp, %ebp
	.cfi_def_cfa_register 5
	andl	$-16, %esp
	subl	$16, %esp
	movl	$.LC0, %eax
	movl	$60, 4(%esp)
	movl	%eax, (%esp)
	call	printf
	movl	$0, %eax
	leave
	.cfi_restore 5
	.cfi_def_cfa 4, 4
	ret
	.cfi_endproc
.LFE0:
	.size	main, .-main
	.ident	"GCC: (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3"
	.section	.note.GNU-stack,"",@progbits

```

---

### Post by spjackson on 2012-07-06
I'm not an assember programmer, but I do know that for a C program there is magic that happens before main() is called. This magic is implementation dependent but usually includes opening of stdin, stdout, stderr. I suspect that you get no output from printf because stdout is not open/initialized.

---

### Post by zapperterrus on 2012-07-06
Yeah! It's all OK! There you are the new correct code:

```

.data
inpf: .string "%d \n"
.text
.globl _start
_start:
movl $56, %eax
movl $4, %ebx
addl %ebx, %eax
pushl %eax
pushl $inpf
call printf
fine:
mov $1, %eax
int $0x80

```



   The function takes a single parameter c when it is a string, if it is a number, first there must be another parameter that identifies!

 In the old code was inserted in the stack, only the number, then call printf corresponded to:
 printf (number);
 That C can not be done!
 In the new code on the stack I have also added another parameter, that always precedes all:
 printf ("% d \ n", number);
 And now it works!

 Excuse me for writing, perhaps incorrectly, I'm Italian and I'm using the google translator.

Thanks to all!!

---

