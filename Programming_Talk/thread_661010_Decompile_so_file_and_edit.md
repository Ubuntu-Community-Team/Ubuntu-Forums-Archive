---
title: "Decompile so file and edit"
date: 2008-01-07
forum: Programming Talk
---

### Post by Erik. on 2008-01-07
Hi everyone,

I am now using ubuntu for almost 5 weeks and i like it very much

I now have a .so file on my computer that i need to decompile and then edit it and then compile it again.

I have downloaded the program and there are options in it that i don't use and i want to delete them...

Can someone help me whit some information about it

Erik

---

### Post by Wybiral on 2008-01-07
First, see if it's open source! If it is, just recompile the object file yourself. If not, I would suggest a disassembler, but the last time a thread on reverse engineering popped up our friendly mods closed it. :)

---

### Post by nick_h on 2008-01-07
Try to see what package it is in by using:
```
dpkg -S /path/filename.so
```
When you find the package download the source for it.

---

### Post by Erik. on 2008-01-07
Hi,

Thanks for posting

It says not found...

But i am sure the file is in the directory

I asked the one who made the file and i can edit it if i want so there is no problem i hope the do not close it :)

---

### Post by ghostdog74 on 2008-01-07
you may also want to try the "strings" command and see what you can see. No guarantee though.
```

strings <your.so file> 

```

---

### Post by Erik. on 2008-01-08
Hi,

Thats works, i get a big big list whit text
Do you now know how it is written or what can i do whit that text? 
Is there still a way to decompile?


Erik

---

### Post by Majorix on 2008-01-08
> **Wybiral said:**
> If not, I would suggest a disassembler, but the last time a thread on reverse engineering popped up our friendly mods closed it. :)

You are probably remembering my thread. Ah the days :D

If I were you, I wouldn't use proprietary software on Linux. And all OSS can be edited to your needs, according to GPL and similar licensing policies. Edit&compile :)

---

### Post by nick_h on 2008-01-08
> I asked the one who made the file and i can edit it if i want so there is no problem
Why don't you ask them for the source code?

---

### Post by Erik. on 2008-01-17
I already asked the source code but he does not response i think he will not return to the forum i find the file.

I think it is an C file but i don't know

Is there a way to get information about the file and see what code it is and then decompile it?

Hope you can help me

---

### Post by Wybiral on 2008-01-17
> **Erik. said:**
> I already asked the source code but he does not response i think he will not return to the forum i find the file.

I think it is an C file but i don't know

Is there a way to get information about the file and see what code it is and then decompile it?

Hope you can help me

Have you ever tried to work on a project without any comments? What about a project with mangled labels? What about a project who's source has been optimized by a compiler?

There is no way to decompile something. Once it's compiled, the labels are lost, the structure is changed, and all you're left with is the assembly representation. There ARE decompilers, but they just give you C-ified assembly (which isn't going to help you much in terms of understanding the code). There are also disassemblers, which will reassemble the machine code into assembly, which is probably your best bet. But if you don't know assembly (very well, and how compilers optimize C code), you're basically out of luck until you can get the source from that guy.

---

