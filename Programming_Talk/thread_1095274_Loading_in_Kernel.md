---
title: "Loading in Kernel"
date: 2009-03-13
forum: Programming Talk
---

### Post by kernelsec09 on 2009-03-13
When a program is loaded into memory (after running it from command line, say), 

1. How does the Linux loader (ld) map the code segment to memory? 

2. For example, the size of the code segment size is 6MB. 
How many pages it creates?

3. Does the i'th page start at codeseg+(i-1)*pagesize; i.e., first page starts at 0 (contains data in 0 to pagesize-1), second page at pagesize and contains pagesize to 2*pagesize-1 and so on. If not, how does it work?

4. Does the first page starts with the first instruction to be executed? Is that the beginning of main()?

5. Consider  an instruction in the binary: OPCODE OPND1 OPND2; If the memory mapping is such that OPCODE lies in page-i and "OPND1 OPND2" lies on page-(i+1), then is it a valid mapping? Or the loader maps the instruction into page-(i+1)?

---

### Post by the_unforgiven on 2009-03-13
> **kernelsec09 said:**
> When a program is loaded into memory (after running it from command line, say), 

1. How does the Linux loader (ld) map the code segment to memory? 

2. For example, the size of the code segment size is 6MB. 
How many pages it creates?

3. Does the i'th page start at codeseg+(i-1)*pagesize; i.e., first page starts at 0 (contains data in 0 to pagesize-1), second page at pagesize and contains pagesize to 2*pagesize-1 and so on. If not, how does it work?

Most of it can be answered with one word:
[ELF]("http://en.wikipedia.org/wiki/Executable_and_Linkable_Format")

> **kernelsec09 said:**
> 
4. Does the first page starts with the first instruction to be executed? Is that the beginning of main()?
First question: Check the ELF specs - it tells you how the binary is laid out and the ld will use it for loading. 

Second question: no.
The glibc contains the startup code that prepares to load your program and pass control to *your* main().

> **kernelsec09 said:**
> 
5. Consider  an instruction in the binary: OPCODE OPND1 OPND2; If the memory mapping is such that OPCODE lies in page-i and "OPND1 OPND2" lies on page-(i+1), then is it a valid mapping? Or the loader maps the instruction into page-(i+1)?
Theoretically, it's a valid mapping, but it is practically very inefficient - so, practically, the linker itself won't generate such a mapping. The linker will use address alignment to lay out the executable - which will guarantee that the instruction is not broken in half as you break the alignment then.

HTH ;)

---

