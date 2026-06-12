---
title: "Need hex machine code file for some sample GRUB source"
date: 2007-06-30
forum: Programming Talk
---

### Post by New-In-Ohio on 2007-06-30
Hello, I'm new to ubuntu, fairly new to programming,  I just installed kubuntu 7.04 on a dual boot machine.  I'm trying to understand GRUB completely.  I've been looking at the MBR with dd output in KHexEdit.  I downloaded the GRUB source and went to the stage1 directory.  What i would like to do is convert stage1.S into "hex formatted" code (not sure how to say that) so i can reverse compile in my mind what is going on step by step.  I want to look at the assembly language and hex code side by side to know for example, "jmp is ebh" and "nop is 90h".  I thought
```
cc -S -o test.s stage1.S
```

would work where 'test.s' is the assembly code.  All I get is the same file output to the screen and no test.s file.  After stumbling and searching I realized my first problem was not enough developement code installed.  I did an 'apt-get install build-essential'.  After this, I moved stage1.h and stage1.S into a bin directory off my home directory and added that to $PATH. Now the output is this

# 1 "stage1.S"
# 1 "<built-in>"
# 1 "<command line>"
# 1 "stage1.S"

and no test.s in the directory.  I cant even do "cc stage1.S" to get a.out.  I know I'm missing something fundamental.  If someone could help or tell me which FriendlyManual to read it would all be appreciated.

---

### Post by New-In-Ohio on 2007-06-30
I solved the hex object file issue by simply doing 
```
cc -c -o test.o stage1.S
```
I feel silly.  Still not sure why the linker isn't working.

Andrew

---

