---
title: "how to write to a particular address in C?"
date: 2013-01-12
forum: Programming Talk
---

### Post by IAMTubby on 2013-01-12
Hello, 
I am trying to write to a specific memory location in C, but I keep getting a segmentation fault.
All the addresses returned are in 7digit hexadecimal, and the address used in the below program (85a9008) was got printing the address from a previous program, which means that writing to this memory location is permitted.

```
#include <stdio.h>

int main(void)
{
  char* address = (int *)0x85a9008;
  *address = 'a';
  printf("\n*address == [%c]",*address);
  printf("Memory address is: 0x%p\n", address);

  return 0;
}

```

Please advise.
Thanks.

---

### Post by bird1500 on 2013-01-12
You can only write to memory allocated and owned by your process.
There are ways to explicitly share memory with other processes, but that's a different story, subject to explicit APIs and limitations.

EDIT: in the old days, back like 20 years ago, you could actually directly access memory of any process, which was a major pain for anyone, except malware programmers.

---

### Post by IAMTubby on 2013-01-12
> **bird1500 said:**
> You can only write to memory allocated and owned by your process.
There are ways to explicitly share memory with other processes, but that's a different story, subject to explicit APIs and limitations.

EDIT: in the old days, back like 20 years ago, you could actually directly access memory of any process, which was a major pain for anyone, except malware programmers.
Thanks bird1500 for the reply. 

1.So how do I find out the list of addresses that can be used by my process ?

2.> your process
Does this mean, my program's executable say a.out that I am executing, or is the list of addresses pre-decided for all C programs or something ?

---

### Post by bird1500 on 2013-01-12
The memory thingy is generally complicated, but in layman's terms:

A program (that is a process) gets automatically some memory from the OS which puts the program into memory and executes it - let's call it static memory that your program can't write to, and probably can't read - not sure about this one.

Then your program once launched can ask the OS (kernel) for memory it can read from and writeto, typically with "malloc()" for C or "new" for C++.

Generally a program doesn't care how much memory it can get from the OS, it only checks if the request for new memory succeeded (and frees it if needed when done), if not - probably the OS is out of memory.

For example, for C:
char *buf = (char*) malloc(10);//allocated 10 bytes somewhere in computer's memory which is called "the heap".
now, buf points to the first char,
buf+5 points to the 6th char,
buf+9 to the last one,
if you try to access buf+10 or more you get an error (segmentation fault or so) because it's outside the range of the chunk of memory you asked for.

---

### Post by bouncingwilf on 2013-01-12
> **bird1500 said:**
> You can only write to memory allocated and owned by your process.
There are ways to explicitly share memory with other processes, but that's a different story, subject to explicit APIs and limitations.

EDIT: in the old days, back like 20 years ago, you could actually directly access memory of any process, which was a major pain for anyone, except malware programmers.


A pain to most maybe but we used to regularly write direct to video ram and bypass the OS on DOS based systems - It was orders of magnitude faster than OS calls for screen handling!

Bouncingwilf

---

### Post by CptPicard on 2013-01-12
> **IAMTubby said:**
> 
1.So how do I find out the list of addresses that can be used by my process ?

To elaborate on this a little; processes (that is, whatever instance of a program you have launched) also operate within so-called virtual memory. The operating system abstracts away actual hardware memory addresses; your process sees essentially a contigous number of addresses that the CPU's memory-mapper then maps to hw addresses. So in that sense the concept of "list of addresses you may use" is a bit flawed.

However, even addressing outside of explicitly reserved memory within the process-specific virtual memory space is a segfault. This is because addresses are just numbers and if the OS + CPU combination can't map some given number to an actual memory location, that's an error.

---

### Post by Bachstelze on 2013-01-13
> **IAMTubby said:**
> 
1.So how do I find out the list of addresses that can be used by my process ?

You can't, as far as I know. Even if you could, that would be of limited usefulness. If you want to obtain a memory address you can write to, use malloc(), or the & operator on an object on the stack.

> 2. Does this mean, my program's executable say a.out that I am executing, or is the list of addresses pre-decided for all C programs or something ?

The textbook definition of a process is "an instance of a program in memory". If you run the same program twice, it will create two distinct processes.

I see you still haven't done any serious reading on operating system. I suggested you do just that a while ago...

---

### Post by xb12x on 2013-01-13
> **IAMTubby said:**
> Hello, 
I am trying to write to a specific memory location in C, but I keep getting a segmentation fault.
All the addresses returned are in 7digit hexadecimal, and the address used in the below program (85a9008) was got printing the address from a previous program, which means that writing to this memory location is permitted.

```
#include <stdio.h>

int main(void)
{
  char* address = (int *)0x85a9008;
  *address = 'a';
  printf("\n*address == [%c]",*address);
  printf("Memory address is: 0x%p\n", address);

  return 0;
}

```

Please advise.
Thanks.


You will have to write a device driver. 

If the address is allocated memory to your application, your application will communicate this virtual address to your driver. The driver will perform the translation of the virtual address, and then do the actual accesses. The driver will then make the results available to your application.

If the address is not allocated memory but is memory-mapped hardware, such as a register of a peripheral device (video, hard-drive, etc) then the driver will first have to get permission to access the physical address.
 
The only exceptions to this that I can think of (in Linux) are certain legacy addresses that allow access from applications using ioperm(). These are things such as legacy serial ports, etc.

---

### Post by ehrt74 on 2013-01-15
What you want to read up on are TLBs and page tables :)

---

### Post by leviteo on 2013-01-16
I agree with [xb12x]("http://ubuntuforums.org/member.php?u=1100284"), to have access a reserved address you will have to write a driver. After that you register drivers on kernel and you will be able to use it from user space.

To use the address in the driver, look for mmap() implementation. It is a start point :)

---

### Post by jwbrase on 2013-01-17
> **bouncingwilf said:**
> A pain to most maybe but we used to regularly write direct to video ram and bypass the OS on DOS based systems - It was orders of magnitude faster than OS calls for screen handling!

Bouncingwilf

Yeah, but as soon as you start multitasking, you end up with programs fighting over the screen if they're allowed to access it directly.

---

