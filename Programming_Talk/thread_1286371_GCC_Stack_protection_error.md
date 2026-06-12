---
title: "GCC Stack protection error"
date: 2009-10-08
forum: Programming Talk
---

### Post by Jeremywilms on 2009-10-08
I have about 11 bytes worth of local variables and I'm getting an error caused by GCC's stack protection. I've been told to link with the -fno-stack-protector flag, but I think that's a dumb solution, unless this issue has to do with an error in GCC. I shouldn't have to disable stack protection to get a couple local variables in a method.

The error is:
```

undefined reference to `__stack_chk_fail'

```

Here's an example that won't compile due to this error. It's actually a more complex routine but I've removed everything but the cause of the error.
```

int vmm_init()
{
	char localVar = 0;
	char buffer[10];

	return 1;
}

```

It's being compiled with the -C flag, and linked with several other object files.

---

### Post by Can+~ on 2009-10-08
This happens with whatever you compile (like, a plain "Hello World!" C main), or the particular case of this function?

Sounds you corrupted something on your stack way before this function executed.

---

### Post by Jeremywilms on 2009-10-08
> **Can+~ said:**
> This happens with whatever you compile (like, a plain "Hello World!" C main), or the particular case of this function?

Sounds you corrupted something on your stack way before this function executed.

That's what I figured, but it's during linking, not while it's executing. After looking into it a bit, here's how I define one of my structs.

```
typedef struct pte_pageTable
{
	pte_pteEntry entries[PAGES_PER_PAGETABLE];
}__attribute__((packed)) PAGETABLE, *PPAGETABLE;

```
typedef unsigned long pte_pteEntry;

The problem here is, I believe the whole struct is being stored in the compiled object file(which is a massive struct). When it is only intended to be used with an allocate region. I.e allocate 4096 bytes at runtime, and have a PPAGETABLE pointer point to the allocated region, It isn't meant to be stored in the object file. I don't think this is the problem, but I'd rather not have the whole struct stored.

---

### Post by Jeremywilms on 2009-10-09
Okay, I managed to recreate the problem in a much smaller scale.
error
```

main.o: In function `main':
main.c:(.text+0x38): undefined reference to `__stack_chk_fail'
main.o: In function `function':
main.c:(.text+0x6b): undefined reference to `__stack_chk_fail'

```

main.c
```

#include "pte.h"
int main()
{
	PPAGETABLE pageTable;
	PPAGETABLE pageTable2;
	char local[12];
	int size = sizeof(PAGETABLE);
	return 0;
}

int function()
{
	char local[12];
	return 1;
}

```

pte.h
```

#pragma once
#define PAGES_PER_PAGETABLE	1024
typedef unsigned long pte_pteEntry;

typedef struct pte_pageTable
{
	pte_pteEntry entries[PAGES_PER_PAGETABLE];
}__attribute__((packed)) PAGETABLE, *PPAGETABLE;

```

make.sh
```

gcc -c main.c -o main.o
ld  -e main -o main.out main.o

```

---

### Post by ibuclaw on 2009-10-09
Try linking in with the libc library.

```
ld -lc -e main -o main.out main.o
```
I believe this will resolve your issue.

Regards
Iain

---

### Post by Jeremywilms on 2009-10-09
> **tinivole said:**
> Try linking in with the libc library.

```
ld -lc -e main -o main.out main.o
```
I believe this will resolve your issue.

Regards
Iain

Thank you, it has, but is there anyway I can decrease the size of the output? And still be able to use sizeof? The file size is rather big when it stores a structure that large, it can be changed to a pointer instead of an array but then sizeof wont give me the correct size, if worst comes to wost comes to worst I can create a macro like 
#define SIZEOF_PAGETABLE sizeof(pte_pteEntry) * PAGES_PER_PAGETABLE

But if there is another solution I'd like to hear it.

---

### Post by MadCow108 on 2009-10-09
what do you mean with size of the output? the size of the executable?

you can use sizeof(struct pte_pageTable) to get the size of the struct

---

### Post by fct on 2009-10-09
> **Jeremywilms said:**
> Thank you, it has, but is there anyway I can decrease the size of the output? And still be able to use sizeof? The file size is rather big when it stores a structure that large, it can be changed to a pointer instead of an array but then sizeof wont give me the correct size, if worst comes to wost comes to worst I can create a macro like 
#define SIZEOF_PAGETABLE sizeof(pte_pteEntry) * PAGES_PER_PAGETABLE

But if there is another solution I'd like to hear it.

I can't think of a better solution. Pointers (dynamic memory) is what you'll have to use to avoid the whole declared struct being incorporated into the compiled executable.

Also, when defining the macro, it would be a good idea to wrap it with parenthesis to avoid adyacent operations affecting the result when the preprocessor replaces it.

#define SIZEOF_PAGETABLE (sizeof(pte_pteEntry) * PAGES_PER_PAGETABLE)

---

### Post by grayrainbow on 2009-10-09
In general:
undefined reference to 'whatever' error, means that linker couldn't find that function, which on its side means you should just put one more .a in your compiler/linker command line.
 
Btw, what should page table mean? First thing that come to mind when seen is that: it is quite possible to not need stack protection(or better sad - to do it by yourself)
 
Edit:
Actually, its rather unusual but, "undefined..." could also means that one forget to implement some of his/her own declared functions.

---

### Post by ibuclaw on 2009-10-09
> **Jeremywilms said:**
> Thank you, it has, but is there anyway I can decrease the size of the output? And still be able to use sizeof? The file size is rather big when it stores a structure that large, it can be changed to a pointer instead of an array but then sizeof wont give me the correct size, if worst comes to wost comes to worst I can create a macro like 
#define SIZEOF_PAGETABLE sizeof(pte_pteEntry) * PAGES_PER_PAGETABLE

But if there is another solution I'd like to hear it.

```
ld -lc -s -e main -o main.out main.o
```
The -s option strips the binary of unneeded symbols.

Regards
Iain

---

### Post by Jeremywilms on 2009-10-09
> **MadCow108 said:**
> what do you mean with size of the output? the size of the executable?

you can use sizeof(struct pte_pageTable) to get the size of the struct
By size of the output, I mean size of the compiled object file.
I can't use the sizeof method if I cange the array to a pointer, because this would give me the incorrect size(or rather, the size I am not looking for)


Thank you all for your help.

---

### Post by MadCow108 on 2009-10-09
the example you gave does not use dynamically allocated memory so the sizeof will work. sizeof only fails when the size is not known at compile time, this means dynamical memory. It is a compile time operator no function in the normal C sense.

just use the sizeof on the struct **definition** not the pointer or the variable, the compiler will determine the size from definition at compile time. (you could also dereference the pointer or use the variable but this obfuscates your code unnecessarily)

if you use dynamic memory you only have two possibilities, save the size as a variable in the program at runtime or terminate the data appropriately.

---

### Post by Jeremywilms on 2009-10-09
Alright, this isn't making any sense at all now. This is all that is in my test main.c

```

int main()
{
	char localVar[12];
	return 0;
}

```

And make.sh
```

gcc -c main.c -o main.o
ld  -e main -o main.out main.o

```

error
```

main.o: In function `main':
main.c:(.text+0x2e): undefined reference to `__stack_chk_fail'


```

---

### Post by Jeremywilms on 2009-10-10
Wow, okay, I just tried adding a source file to my main project with a function containing a local buffer of 15 bytes and it gave me the stack fault crap. When I link with lc, it works, however the output file is about 246 MB, a normal build it's 17kb.

Anyone know why this would be happening?

---

### Post by Arndt on 2009-10-10
> **Jeremywilms said:**
> Alright, this isn't making any sense at all now. This is all that is in my test main.c

```

int main()
{
	char localVar[12];
	return 0;
}

```

And make.sh
```

gcc -c main.c -o main.o
ld  -e main -o main.out main.o

```

error
```

main.o: In function `main':
main.c:(.text+0x2e): undefined reference to `__stack_chk_fail'


```

```
$ gcc -o main.out main.o
$ ls -l main.out
-rwxr-xr-x 1 arndt arndt 9155 2009-10-10 16:58 main.out
$

```

Why do you use 'ld' for linking?

---

### Post by MadCow108 on 2009-10-10
edit: did something wrong

---

### Post by Jeremywilms on 2009-10-10
Madcow I'll try your suggestion.

Arndrt I need to use ld for linking because I need to speicfy where in memory the kernel is loaded so the linker can(I assume) resolve offsets. I'm writing a kernel, and thus I can't have the compiler assume the origin.
[B]
Edit:[/B]
I didn't get a chance to see your suggestion madcow.

---

### Post by Jeremywilms on 2009-10-10
Alright, I think I'm going to disable the stack protector in GCC, and later possibly write my own. Thank you all for your help.

---

