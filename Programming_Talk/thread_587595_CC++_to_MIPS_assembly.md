---
title: "C/C++ to MIPS assembly"
date: 2007-10-22
forum: Programming Talk
---

### Post by rbprogrammer on 2007-10-22
**does any one know of a program that will convert C/C++ to MIPS assembly??**

i know i can do a gcc or a g++ like:
```
$gcc -S somefile.c
```
and it will take the C file and convert it to assembly.. but that assembly is the x86 assembly (or whatever it is called).

**is there a way to make gcc or g++ make a MIPS assembly file??**

i only ask because of a course here that i am taking that makes us look at MIPS assembly and C code.  it will also be helpful to see "efficient" code.  since i'm still new at the assembly programming, it is still hard to see how to make code efficient since assembly is soooooo much different than any other language that i know.

---

### Post by LaRoza on 2007-10-22
I don't think so, you can't even get NASM out of it, but the assembly languages can't be that different. What syntax is the assembly you are learning?

---

### Post by rbprogrammer on 2007-10-22
ok, when you type out this simple C file: (named test.c)
```

int main()
{
    register int i = 5;
    register int j = 15;
    register int k = i + j;
    return 0;
}

```
then do
```
$ gcc -S test.c
```
you get:
```

	.file	"test.cpp"
	.text
	.align 2
.globl main
	.type	main, @function
main:
.LFB2:
	leal	4(%esp), %ecx
.LCFI0:
	andl	$-16, %esp
	pushl	-4(%ecx)
.LCFI1:
	pushl	%ebp
.LCFI2:
	movl	%esp, %ebp
.LCFI3:
	pushl	%ecx
.LCFI4:
	movl	$0, %eax
	popl	%ecx
	popl	%ebp
	leal	-4(%ecx), %esp
	ret
.LFE2:
	.size	main, .-main
.globl __gxx_personality_v0
	.ident	"GCC: (GNU) 4.1.2 (Ubuntu 4.1.2-0ubuntu4)"
	.section	.note.GNU-stack,"",@progbits

```
now i'm not so sure exactly what any of that means, but in MIPS, the equivalent to the simple addition statement would be:
[INDENT]
register $t0 contains the [FONT="Courier New"]i[/FONT] variable
register $t1 contains the [FONT="Courier New"]j[/FONT] variable
register $t2 contains the [FONT="Courier New"]k[/FONT] variable
[/INDENT]
```

add $t2, $t0, $t1

```
now, i dont know where that step is taking place in the generated assembly code, because i was thinking about just learning a little bit about the x86 assembly then convert it to the MIPS, and view the "efficient" code that way.

---

### Post by LaRoza on 2007-10-22
> **rbprogrammer said:**
> ok, when you type out this simple C file: (named test.c)
```

int main()
{
    register int i = 5;
    register int j = 15;
    register int k = i + j;
    return 0;
}

```


```

add $t2, $t0, $t1

```


These are not the same. In the C version, you have:

A function that starts with the program, and returns an integer, four variables, that **might** be in a register. gcc takes that as a hint, but doesn't have to do it. Also, that operation of adding two integers, and storing them in a variable is a little more complicated in assembly.

There are also other considerations with C, like command line arguments are passed to by the OS.

This is why assembly is good to know, so you can understand the "magic" C and other HLL's.

---

### Post by rbprogrammer on 2007-10-22
> **LaRoza said:**
> 
...
A function that starts with the program, and returns an integer, four variables, that **might** be in a register. gcc takes that as a hint, but doesn't have to do it.
...

well, i tried to make them a register so that i can more easily see how to write an assembly program.  since we use registers a lot (which is probably a necessity for any assembly language) i thought it would be easer to see how the x86 uses registers.

also, i found that on [http://gcc.gnu.org/](http://gcc.gnu.org/) they make a MIPS compiler, so would i be able to install something that would allow me to use my compiler now to make a MIPS file??  like a patch or something??

---

### Post by ankursethi on 2007-10-22
You might want to build yourself a cross compiler, ie, a compiler that produces binaries for another architecture. Now I don't have experience with doing this, so you might want to look around the web a bit. Wikipedia is a good starting point. The GCC mailing lists/IRC channel might be helpful.

---

### Post by mjwood0 on 2007-10-23
This is absolutely correct.

It's not an easy process, but I've successfully created a cross compiler which would target PowerPC from an Intel machine.

Do a google for GCC Cross Compiler and see what you come up with.

---

### Post by psychicist on 2007-10-23
You can create a cross compiler, which will take some time and effort. If you have a powerful machine a much easier way to get a complete MIPS machine is QEMU. You can find the directions to get a MIPS machine setup at [http://www.aurel32.net/info/debian_mips_qemu.php](http://www.aurel32.net/info/debian_mips_qemu.php).

---

