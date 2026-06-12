---
title: "processor fault in C program, what is this??"
date: 2008-11-03
forum: Programming Talk
---

### Post by kcode on 2008-11-03
Im am writing a simple program to implement graphs, using turboc.
At one point i am getting this message at run time:

```

General Protection Exception
0x2357:0x379F

KCODE_GRAPH(1) 0x2357:0x379f Processor Fault

```
Also got a linker warning stating that, no module defination specified: using defaults.

What and why is this? :confused:

thanks

---

### Post by kcode on 2008-11-03
Well, there was an error of ampersand while using scanf().
But what does this error mean ??

---

### Post by WW on 2008-11-03
It probably means your program tried to access memory that it is not allowed to access.  A misplaced ampersand could cause that.

---

### Post by kcode on 2008-11-03
> **WW said:**
> It probably means your program tried to access memory that it is not allowed to access.  A misplaced ampersand could cause that.

Can you quantitatively explain this, using information i provided?

thanks

---

### Post by WW on 2008-11-03
If you showed the code that caused the problem, I (or some other forum member with sharper eyes and better C skills) might be able to explain exactly what caused the error.

---

### Post by themusicwave on 2008-11-03
As was mentioned above by WW, this is most likely caused by your program trying to access memory that wasn't allocated to it.

Basically, when a program is created and run the OS gives it a chunk of memory.  As a protective mechanism, the OS also won't let any program access memory outside of its own allocated block.

This is because if a program could access another program's memory it could do very nasty things like steal information or just plain mess up the other program.

So to protect the user and the other programs on the system, when any program tries to access memory that isn't in its allocated block, the OS assumes that program has some sort of malevolent intent or error in it and kills it instantly.

When this happens this will produce a General Protection Fault.  There could be other causes for this error, but without the code we have no way to know.

Most likely you have a pointer that tried to access the wrong address.

---

### Post by kcode on 2008-11-04
> **themusicwave said:**
> 
Most likely you have a pointer that tried to access the wrong address.

Yaa...as i said i forgot to use an ampersand in scanf().

so if i do :

```

int integer;

scanf("%d",integer);

```

In this case integer points to some address in memory which is not allocated to the program under consideration. Which leads to General Protection Fault(runtime error).
(windows calls this error: General Protection Fault
while linux calls this error: segmentation fault)

Correct me if i'm wrong.

thanks

---

### Post by Zugzwang on 2008-11-04
> **kcode said:**
> 
Correct me if i'm wrong.


Almost... this *might* lead to a General Exception fault but might also lead to unexpected behaviour because the address might actually be valid.

---

