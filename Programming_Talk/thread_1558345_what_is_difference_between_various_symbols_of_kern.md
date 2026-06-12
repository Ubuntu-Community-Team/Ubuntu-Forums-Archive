---
title: "what is difference between various symbols of kernel"
date: 2010-08-22
forum: Programming Talk
---

### Post by jamesbon on 2010-08-22
I was going through some exercise given in my school.I have read the C book but I am not able to understand some part.
That is static variable.
What exactly is a static variable and what does it do?
I saw in Linux Kernel Programming
external and exported are also some thing.
I am not getting the difference between static,EXPORT_SYMBOL,external variable types.
If I make a kernel module then how will I make sure that my variable is visible to the kernel.Is this what it is all talking about?
I have checked this page
[http://en.wikipedia.org/wiki/Static_variable](http://en.wikipedia.org/wiki/Static_variable)

---

### Post by Rinzwind on 2010-08-22
> 14. Static variables

14.1 Overview

Linux is written in ''C'' language, and as every application has:

Local variables
Module variables (inside the source file and relative only to that module)
Global/Static variables present in only 1 copy (the same for all modules)
When a Static variable is modified by a module, all other modules will see the new value.

Static variables under Linux are very important, cause they are the only kind to add new support to kernel: they typically are pointers to the head of a list of registered elements, which can be:

added
deleted
maybe modified

[http://tldp.org/HOWTO/KernelAnalysis-HOWTO-14.html](http://tldp.org/HOWTO/KernelAnalysis-HOWTO-14.html)

Here you can find anything you need to know:
[http://tldp.org/HOWTO/KernelAnalysis-HOWTO.html](http://tldp.org/HOWTO/KernelAnalysis-HOWTO.html)

---

### Post by worksofcraft on 2010-08-22
Main difference is that a static variable has it's memory allocated permanently at COMPILE time... so they last from when they are first encounterd until program exits.

Most other variables last only for teh duration of the block they are allocated in while "heap" variables can be created and destroyed at will.

static variables have the added symptom that their name is not known outside of the module where they are defined.

update: Try this program and it will tell you the sequence of when various objects get created.

```

// ok I'm using C++ because I can make constructors and destructors tell you
// exactly when an object is created and when it is destroyed, but I will try
// not to use anything else that is beyond ordinary C.
// compile this as g++ static.cc and run it as ./a.out
#include <stdio.h>

struct MyObject {
	const char *m;
	MyObject(const char *msg): m(msg) {
		printf("constructing %s\n", m);
	}
	~MyObject() {
		printf("destrucrting %s\n", m);
	}
};

void procedure() {
	MyObject pA = "procedure's automatic pA";
	static MyObject pS = "procedure's static pS";
	// do whatever, and then exit
}

static MyObject mS = "module static mS";

int main() {
	MyObject mA = "main's automatic mA";
	procedure();
}

```

---

### Post by Sylslay on 2010-08-22
THANX for last link, added to my bookmarks and meaby read.

---

### Post by jpaugh64 on 2010-08-22
The term "static" actually means something different when it is in a file or when it is in a function. Be careful because many things in C are like that: it makes more sense to the compiler than to the programmer.

I know that "static" *inside of a function* causes the variable it modifies to keep the same value for different calls to that function. Static *inside a file* (but outside any function) affects the ability of other code to see it.

---

### Post by nvteighen on 2010-08-22
> **jpaugh64 said:**
> The term "static" actually means something different when it is in a file or when it is in a function. Be careful because many things in C are like that: it makes more sense to the compiler than to the programmer.

I know that "static" *inside of a function* causes the variable it modifies to keep the same value for different calls to that function. Static *inside a file* (but outside any function) affects the ability of other code to see it.

I'm not sure if that difference actually exists.

What **static** does is to create a label for a certain global memory chunk and give that a value at compile time, plus **not** making it available to the linker.

Look at these examples:


```

static int mystatic = 6;

int main(void)
{
    return 0;
}

```

Generated ASM is as follows:
```

	.file	"static2.c"
	.data
	.align 4
	.type	mystatic, @object
	.size	mystatic, 4
mystatic:
	.long	6
	.text
.globl main
	.type	main, @function
main:
	pushl	%ebp
	movl	%esp, %ebp
	movl	$0, %eax
	popl	%ebp
	ret
	.size	main, .-main
	.ident	"GCC: (Debian 4.4.4-8) 4.4.5 20100728 (prerelease)"
	.section	.note.GNU-stack,"",@progbits

```

Compare that with declaring the global variable as non-static:
```

int mynonstatic = 6;

int main(void)
{
    return 0;
}

```

```

	.file	"nonstatic2.c"
.globl mynonstatic
	.data
	.align 4
	.type	mynonstatic, @object
	.size	mynonstatic, 4
mynonstatic:
	.long	6
	.text
.globl main
	.type	main, @function
main:
	pushl	%ebp
	movl	%esp, %ebp
	movl	$0, %eax
	popl	%ebp
	ret
	.size	main, .-main
	.ident	"GCC: (Debian 4.4.4-8) 4.4.5 20100728 (prerelease)"
	.section	.note.GNU-stack,"",@progbits

```

The only difference is that in the non-static case, there's the **.globl mynonstatic** that makes that symbol available to the linker.

Now, careful observation will make you notice that both global variables are declared as labels, exactly the same way as main is. ASM doesn't really distinguish between functions and variables (the @function and @object thing is just an optimization gcc does): all there is memory addresses that you conveniently can refer to with a label. So, when you declare a function static, what will happen is exactly the same: the function is given a value (its code) and make it unavailable to the linker... exactly what was done to the variable.

Here you have the C and ASM for a static function:
```

	.file	"stat_func.c"
	.text
	.type	something, @function
something:
	pushl	%ebp
	movl	%esp, %ebp
	movl	$0, %eax
	popl	%ebp
	ret
	.size	something, .-something
	.ident	"GCC: (Debian 4.4.4-8) 4.4.5 20100728 (prerelease)"
	.section	.note.GNU-stack,"",@progbits

```

Again, the value for something is its code, it's a global value but not available to the linker because there's no **.globl something**.

What about local static variables? Actually, the idea of local variables is lost when compiling C to ASM. What you have is a global stack that each function is in charge to clean up when returning... therefore making its local values no longer available outside the function... but place a jmp and the value will be available. What happens with static variables is that the static again sets up a value at compile time and makes the symbol unavailable for the linker... as you'll see here:

```

int main(void)
{
    static int mystatic = 6;
    
    return 0;
}

```

```

	.file	"static.c"
	.text
.globl main
	.type	main, @function
main:
	pushl	%ebp
	movl	%esp, %ebp
	movl	$0, %eax
	popl	%ebp
	ret
	.size	main, .-main
	.data
	.align 4
	.type	mystatic.1248, @object
	.size	mystatic.1248, 4
mystatic.1248:
	.long	6
	.ident	"GCC: (Debian 4.4.4-8) 4.4.5 20100728 (prerelease)"
	.section	.note.GNU-stack,"",@progbits

```

The only difference here is that the .data section has been placed *after* the main "rets" (a kind of return you have in ASM...)... ASM indentation is awful here, but actually main ends at the ret, not at the mystatic.1248 label. Ok, I'm not sure why the name is "mangled" but it's clear that the variable is declared as global even when we declared it as local in C. What will happen is that the C compiler will restrict the usage of that symbol to the main function, but you clearly see that it's just a way to create the illusion of locality... It's actually a global and that's why its value is persistent across the program's execution.

So, in summary, it seems that the real effective meaning (I don't care what the standard says) of static is "Make a global memory address not be available to the linker"... therefore we can explain why is it used both for functions and variables.

Of course, tutorials are doing fine to explain this the way they do... As you see, you have to step down to ASM in order to make some sense of this. Also, this is another great reason of why C is such a pain to use: in the end you still have to understand the basics of ASM... while to use bash, Perl, Python you don't need to know C (or the language the implementation is written in).

EDIT P.S.: Of course, this is true only for gcc. It'd be interesting to see how other compilers do this. But I doubt we'll find any major difference.

---

### Post by jamesbon on 2010-08-28
That was really great.Thanks for such a nice explanation.

---

