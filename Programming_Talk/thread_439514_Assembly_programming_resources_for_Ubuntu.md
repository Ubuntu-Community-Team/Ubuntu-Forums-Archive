---
title: "Assembly programming resources for Ubuntu?"
date: 2007-05-10
forum: Programming Talk
---

### Post by keantoken on 2007-05-10
Hello.

I need some good resources (MUST be FREE and ONLINE) about programming in assembly language with Ubuntu. Here is a list of all I need:

1: How to use interrupts.

2: System call table which explains the system calls and their functions.

3: How to interface assembly with the OSS or ALSA and other resources.

4: A good assembler for linux similar to the Flat Assembler (preferably with a GUI).

I will be trying to find these myself and will edit this post (if forum rules allow) to delete the ones I've already found. Thanks for all suggestions!

 - keantoken

---

### Post by JNowka on 2007-05-10
I know that you can download nasm from the repos, and search google for a good nasm tutorial.  I hope this helps at least a little

---

### Post by medya on 2007-05-10
I installed NASM but  it doestn compile the program ... it gives me plent of syntax errors !
it work fine in windows using MASM 

can somebody help me?
how to compile my program so it doesnt give me syntax errors....

---

### Post by Siph0n on 2007-05-11
You might want to post atleast some of your code :)

---

### Post by jamescox84 on 2007-05-11
That's a good point, because there are at lease two kinds of syntax for assemble language on x86 (that I can think of) and if you use the wrong one with the wrong assembler then you'll run into problems.

These are GAS and NASM. In fact most assembler have different subtleties in syntax, but GAS and NASM are the main assemblers used under Linux. Try assembling you code with GAS to see if your using GAS's syntax. 

```

as your_source_file_here.S

```

---

### Post by Wybiral on 2007-05-11
Basically, if you see a bunch of "$" and "%" everywhere, and some of the opcodes are postfixed with "l" or "b" it's GAS.

If not, and it's for Linux, then it's NASM.

Interrupts? Well, look for a chart of the sys_calls. The command that makes the actual system call is "int 0x80" and the sys_call is defined by the value of "eax". So if the system exit call is "1", then...
```

mov eax, 1
int 0x80

```
That will exit.
Just look for a chart on the system calls.

If you want to use ALSO and OSS, then you need a good C interface. Possibly their development files, if not, then you can write your own small wrapper to make assembly interfacing easier. Then you just need to link to those object files.

I never was much of a fan of FASM, but NASM is *close*. It doesn't have an IDE, but how much would an IDE help for assembly?

---

### Post by uvaraj6 on 2010-12-18
[http://www.securitytube.net/Assembly-Primer-for-Hackers-(Part-1)-System-Organization-video.aspx](http://www.securitytube.net/Assembly-Primer-for-Hackers-(Part-1)-System-Organization-video.aspx)

The best Free asm tutorial available in the Internet

---

### Post by keantoken on 2010-12-18
Thanks, you must be trying to creep me out though since this thread has been dead for 2 years. :D

 - keantoken

---

### Post by semperfried76 on 2012-09-19
Thanks, just what I was looking for! Got NASM installed on Quantal.

---

