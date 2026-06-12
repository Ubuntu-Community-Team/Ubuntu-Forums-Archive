---
title: "Memory management in C on *NIX"
date: 2011-03-10
forum: Programming Talk
---

### Post by cguy on 2011-03-10
**1st issue:**
The initialized global and static variables are placed in that part of the data space dedicated to initialized values.

Where do the initialized LOCAL variables get stored?

**2nd issue:**
like above, but for the uninitialized LOCAL variables and the BSS segment.

**3rd issue:**
Say you point a pointer *p to the location 0xA56F (totally random).
Would this value point to a location in the real memory or in the virtual mem?

If every pointer points to a location in the process' virtual memory, why do they say that if random access to the memory were allowed you could crash/cause a security problem in your SYSTEM?

---

### Post by Arndt on 2011-03-10
> **cguy said:**
> **1st issue:**
The initialized global and static variables are placed in that part of the data space dedicated to initialized values.

Where do the initialized LOCAL variables get stored?

**2nd issue:**
like above, but for the uninitialized LOCAL variables and the BSS segment.

**3rd issue:**
Say you point a pointer *p to the location 0xA56F (totally random).
Would this value point to a location in the real memory or in the virtual mem?

If every pointer points to a location in the process' virtual memory, why do they say that if random access to the memory were allowed you could crash/cause a security problem in your SYSTEM?

1) Do you mean those prefixed by 'static'? They are in the same area as the global ones. If you mean stack variables, code is emitted to initialize them at runtime.

2) I'm not certain, but you can get a lot of information out of the linker with some extra arguments. See "man ld".

3) Virtual memory, of course.

I don't know what "they" are saying, but it sounds like they mean that if every program had free access to the real memory, then there would be security problems and crashes.

---

### Post by Simian Man on 2011-03-10
> **cguy said:**
> **1st issue:**
The initialized global and static variables are placed in that part of the data space dedicated to initialized values.

Where do the initialized LOCAL variables get stored?
They are allocated dynamically on the stack when the function containing them is called.  They are then given their initial value dynamically as well, unlike initialized static variables.


> **cguy said:**
> 
**2nd issue:**
like above, but for the uninitialized LOCAL variables and the BSS segment.
Uninitialized locals are also allocated on the stack dynamically, but there value will just be whatever was on the stack already.  The BSS segment is like the data segment, but without initialized values.  Some architectures will only store the size of the BSS segment in the object code to save space.


> **cguy said:**
> 
**3rd issue:**
Say you point a pointer *p to the location 0xA56F (totally random).
Would this value point to a location in the real memory or in the virtual mem?
Virtual.  User space programs *never* deal with physical memory addresses.

> **cguy said:**
> If every pointer points to a location in the process' virtual memory, why do they say that if random access to the memory were allowed you could crash/cause a security problem in your SYSTEM?

Who says that?  Maybe they are speaking loosely, or maybe the source is out of date.  You are correct, with modern OSs, is isn't possible for one process to corrupt another's memory.

---

### Post by cguy on 2011-03-13
Thanks you for the explanations.

**4th issue:** where do pointers get stored?
eg:
[php]
int *p; // p is NULL; does it go in bss or the initialized data segment?
int *p = (int *)malloc(sizeof(int)) // how about this one?
int *p = "Hello!"; // I suppose this one goes in the data segment, right?
[/php]

**and arrays?**
[php]int a[20];
int a[2]={1,3};[/php]

Edit: and is there a memory analysis tool so I can figure these out myself?

---

### Post by MadCow108 on 2011-03-13
all pointers and the array in that example are on the stack (unless their global).
the malloc'd memory is on the heap. in your example the pointer to it is on the stack, but it also can be on the heap if you wish.
```

{
int * a = malloc(sizeof(int*)) // stack pointer to heap memory
*a = malloc(sizeof(int) // heap pointer to heap memory
}
```

no need for a tool for this:
uninitialized global, static => uninitialized data segment (bss)
initialized global, static => initialized data segment (data/text)
malloc'd => heap
all else => stack

---

### Post by cguy on 2011-03-13
I'm sorry, but that didn't quite clear it for me.

Suppose every variable is global.
**int *p;** pointers are initialized to NULL. Is this enough to store it to the data segment?

**int *p = "Hello!";** Hello! is a constant and it will be stored in the data segment. p will point to the memory location of the letter "H", therefore p will also be stored on the data segment, right?

**int *p = (int *)malloc(sizeof(int));** The memory which p will point to is undefined at compilation time; makes sense if p will be stored on the stack.

But for this: (your example)
***a = malloc(sizeof(int);** Why is a stored on the heap and not the stack?


As for the arrays, considered global, I am still confused. (int a[10] goes in bss and int b[2]={5,7} in the data segment?)

---

### Post by MadCow108 on 2011-03-13
read this, it has all your questions answered:
[http://en.wikipedia.org/wiki/Data_segment](http://en.wikipedia.org/wiki/Data_segment)
also look at the references

if you do not understand, stop caring.
besides knowing stack and heap these are details you do not need in practice unless your going really low level (like compiler/linker writing).

---

### Post by ibuclaw on 2011-03-13
Global symbols without default initialisers go in the bss segment; ditto with default initialisers go in the data segment.

Just as threaded global symbols without default initialisers go in the tbss segement; ditto with default initialisers go in the tdata segment.

Local or scope variables are inited on the stack.
Dynamically allocated memory on the heap (alloca being the only exception).

Nothing else to it. :)

---

