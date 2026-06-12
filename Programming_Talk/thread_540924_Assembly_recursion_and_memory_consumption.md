---
title: "Assembly recursion and memory consumption"
date: 2007-09-02
forum: Programming Talk
---

### Post by xlinuks on 2007-09-02
Hi, I'm currently learning assembly.
I have the following recursion (from a book) which computes the factorial of 4 (the code itself is not too important in our case, the main idea is that it contains an example of a recursion)::
```

.section .data
.section .text

.globl _start
.globl factorial
_start:
    pushl $4
    call factorial
    addl $4, %esp
    movl %eax, %ebx
    movl $1,  %eax
    int $0x80
    
    .type factorial, @function
    factorial:
        pushl %ebp
        movl %esp, %ebp
        
        movl 8(%ebp), %eax
        cmpl $1, %eax
        je end_factorial
        
        decl %eax
        push %eax
        call factorial
        movl 8(%ebp), %ebx
        imull %ebx, %eax
        
        end_factorial:
        movl %ebp, %esp
        popl %ebp
        
        ret

```
Every time when the function gets called (in this case from inside itself) a new stack frame is created/allocated, and the old stack frame of the functions called before don't get dismissed because they will quit after the control returns to them. Does that mean that we have an explosion of portions of RAM consumption? I mean - for a while we create a bunch of stack frames. What if it wasn't 4 but 2000000000 (2 billion) ?
Am I missing some point? Please help.

---

### Post by CptPicard on 2007-09-02
> **xlinuks said:**
> Does that mean that we have an explosion of portions of RAM consumption?

In short, yes. :) Welcome to the wonderland of unoptimized tail recursion. This is why you will prefer to implement factorial as a loop, because you can.

(I wouldn't call it an explosion, though. It's just linear growth. Try something with exponential time for an example of explosion -- those usually run in log space though :) )

---

### Post by xlinuks on 2007-09-02
Thanks a lot, that's the question that's been plaguing me while learning that chapter of the book - ain't it too expensive and slow compared to a loop?
I feel better now :)

---

### Post by aks44 on 2007-09-02
> **xlinuks said:**
> What if it wasn't 4 but 2000000000 (2 billion) ?

As a side note, if you tried to compute the factorial of 2 billion, you'd overflow 32-bit integers at 13!, and as a wild guess I'd say that 64-bit integers overflow somewhere around 20!.

Given that the result wouldn't be correct in any case, I wouldn't bother too much about the stack frames...

Better do the multiplication beforehand, check the overflow bit, and exit with an error if it is set. ;)

---

